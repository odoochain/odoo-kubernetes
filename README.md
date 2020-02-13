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

--allow-privileged=true

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
正规流程

    git status（查看本地分支文件信息，确保更新时不产生冲突）

    git checkout – [file name] （若文件有修改，可以还原到最初状态; 若文件需要更新到服务器上，应该先merge到服务器，再更新到本地）

    git branch（查看当前分支情况）

    git checkout remote branch (若分支为本地分支，则需切换到服务器的远程分支)

    git pull
————————————————

快速流程

上面是比较安全的做法，如果你可以确定什么都没有改过只是更新本地代码
1. git pull (一句命令搞定)

git branch 看看分支
git chechout aaa 切换分支aaa
git branck aaa 创建aaa分支
git chechout -b aaa 本地创建 aaa分支，同时切换到aaa分支。只有提交的时候才会在服务端上创建一个分支
————————————————
版权声明：本文为CSDN博主「futuretodaylonggong」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/longlc123/article/details/78652569
