# install k8s cluster at gcp manual
https://github.com/latermonk/install-k8s-cluster-the-manual-way/tree/master/docs


# ssh

https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys#locatesshkeys


##  Create new ssh-key



## windows

### PUTTY
![win_sshkey01](images/win_sshkey01.png)

因此公钥为：


```
ssh-rsa [KEY_VALUE] [USERNAME]
```
其中：

KEY_VALUE 是 生成的公钥的值      
USERNAME  是需要使用的用户名     

### XSHELL


![shell-keygen001](images/shell-keygen001.png)


## Upload pub key to server


![shell-keygen002](images/shell-keygen002.png)


## XSHELL连接


![shell-keygen003](images/shell-keygen003.png)

![NEXT](01-prerequisites.md)