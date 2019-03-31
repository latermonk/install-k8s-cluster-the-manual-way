
```
./scripts/generate-kubeconfig-kube-proxy
./scripts/generate-kubeconfig-worker
```


## 01 generate-kubeconfig-kube-proxy


```
kubectl config set-cluster kubernetes-the-hard-way \
  --certificate-authority="${dir}/../certificates/ca.pem" \
  --embed-certs=true \
  --server=https://192.168.199.10:6443 \
  --kubeconfig="${dir}/../config/kube-proxy.kubeconfig"


```

```
kubectl config set-credentials kube-proxy \
  --client-certificate="${dir}/../certificates/kube-proxy.pem" \
  --client-key="${dir}/../certificates/kube-proxy-key.pem" \
  --embed-certs=true \
  --kubeconfig="${dir}/../config/kube-proxy.kubeconfig"
```


```
kubectl config set-context default \
  --cluster=kubernetes-the-hard-way \
  --user=kube-proxy \
  --kubeconfig="${dir}/../config/kube-proxy.kubeconfig"

```


```

kubectl config use-context default --kubeconfig="${dir}/../config/kube-proxy.kubeconfig"
```




## 02 generate-kubeconfig-worker


```
for instance in worker-0 worker-1 worker-2; do
  kubectl config set-cluster kubernetes-the-hard-way \
    --certificate-authority="${dir}/../certificates/ca.pem" \
    --embed-certs=true \
    --server=https://192.168.199.40:6443 \
    --kubeconfig="${dir}/../config/${instance}.kubeconfig"

  kubectl config set-credentials system:node:${instance} \
    --client-certificate="${dir}/../certificates/${instance}.pem" \
    --client-key="${dir}/../certificates/${instance}-key.pem" \
    --embed-certs=true \
    --kubeconfig="${dir}/../config/${instance}.kubeconfig"

  kubectl config set-context default \
    --cluster=kubernetes-the-hard-way \
    --user=system:node:${instance} \
    --kubeconfig="${dir}/../config/${instance}.kubeconfig"

  kubectl config use-context default --kubeconfig="${dir}/../config/${instance}.kubeconfig"
done
```



