# k3s部署测试

本次环境
- 192.168.100.101（部署机）
- 192.168.100.102（worker）

### 1、准备镜像
- cnrancher/autok3s:v0.5.2
- rancher/k3d-proxy:5.2.2
- rancher/k3s:v1.21.7-k3s1

### 2、部署autok3s
```
docker run -itd --restart=unless-stopped --net host -v /var/run/docker.sock:/var/run/docker.sock --name=k3s-demo cnrancher/autok3s:v0.5.2
```
可访问web端
192.168.100.101:8080

### 3、拉起k3s
```
autok3s -d create \
    --provider native \
    --name myk3s \
    --ssh-user root \
    --ssh-password "111111" \
    --master-ips 192.168.100.101,192.168.100.102 \
    --worker-ips 192.168.100.101
```
