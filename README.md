# docker_on_ubuntu
How to install docker desktop on Ubuntu 
[based_on_this](https://docs.docker.com/desktop/install/linux/)

## Steps
1. sudo apt install gnome-terminal
2. Set up Docker's apt repository.
```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
2. Download the latest DEB package. [link](https://desktop.docker.com/linux/main/amd64/docker-desktop-amd64.deb?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-linux-amd64)
3. Install the package with apt as follows:
```bask
sudo apt-get update
sudo apt-get install ./docker-desktop-<arch>.deb
```
4. Sets the capability on the Docker Desktop binary to map privileged ports and set resource limits.
get path to docker
```bash
which docker
```
check if it's not a symlink
```bash
ls -l PATH
```
setcap on the actual binary:
```bash
sudo setcap 'cap_net_bind_service,cap_sys_resource=eip' /PATH/TO/ACTUAL/BINARY
```
5. 
