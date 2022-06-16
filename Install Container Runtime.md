# Install Container Runtime ( for all Machine )

1. Update apt package
    
    ```bash
    sudo apt-get update && sudo apt-get upgrade
    ```
    
2. Install Docker
    
    ```bash
    curl https://get.docker.com/ | sh
    ```
    
3. Check Docker version
    
    ```bash
    docker version
    ```
    
4. Change docker Cgroup, default value is `Cgroup Driver: cgroupfs`
    
    ```bash
    sudo cat <<EOF | sudo tee /etc/docker/daemon.json
    { "exec-opts": ["native.cgroupdriver=systemd"],
    "log-driver": "json-file",
    "log-opts":
    { "max-size": "100m" },
    "storage-driver": "overlay2"
    }
    EOF
    ```
    
5. Restart Docker service
    
    ```bash
    sudo systemctl restart docker
    ```
    
6. Check Cgroup Docker
    
    ```bash
    sudo docker info | grep -i cgroup
    ```
    
    ```bash
    Cgroup Driver: systemd
    Cgroup Version: 1
    ```
    

7. Change permission

    ```bash
    sudo usermod -aG docker $USER
    ```

8. Reboot instance
    
    ```bash
    sudo reboot
    ```
