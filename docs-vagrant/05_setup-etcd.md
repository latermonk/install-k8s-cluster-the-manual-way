## 


```
for i in {0..2}; do
  cat <<EOF | vagrant ssh "controller-${i}" -- sudo bash

cp "/vagrant/tools/etcd-${etcd_version}-linux-amd64/etcd"* /usr/local/bin

mkdir -p /etc/etcd /var/lib/etcd

cp \
  /vagrant/certificates/ca.pem \
  /vagrant/certificates/kubernetes-key.pem \
  /vagrant/certificates/kubernetes.pem \
  /etc/etcd/
cp \
  "/vagrant/config/\$(hostname)-etcd.service" \
  /etc/systemd/system/etcd.service

systemctl daemon-reload
systemctl enable etcd
systemctl start etcd
EOF
done
```

