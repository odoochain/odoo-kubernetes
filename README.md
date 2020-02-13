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
```
sudo vim /var/snap/microk8s/current/args/kube-apiserver
```
Add `--allow-privileged option`

Restart MicroK8s
```
microk8s.stop
microk8s.start
```
Apply YAML config
```
microk8s.kubectl apply -f microk8s/odoo.yaml
```
正规流程

    git status（查看本地分支文件信息，确保更新时不产生冲突）

    git checkout – [file name] （若文件有修改，可以还原到最初状态; 若文件需要更新到服务器上，应该先merge到服务器，再更新到本地）

    git branch（查看当前分支情况）

    git checkout remote branch (若分支为本地分支，则需切换到服务器的远程分支)

    git pull
————————————————
