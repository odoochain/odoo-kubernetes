Odoo on Kubernetes
---

####
Running Odoo on MicroK8s:

Install MicroK8s https://microk8s.io/
```
sudo snap install microk8s --classic
```

Enable persistent storage
```
microk8s.enable storage
```
Edit config to allow support Odoo with root privileges
Add this line to the following 2 config files.

–allow-privileged=true

```
sudo vim /var/snap/microk8s/current/args/kubelet
sudo vim /var/snap/microk8s/current/args/kube-apiserver
```


Restart MicroK8s
```
microk8s.stop
microk8s.start
```
Apply YAML config
```
microk8s.kubectl apply -f microk8s/odoo.yaml
```
