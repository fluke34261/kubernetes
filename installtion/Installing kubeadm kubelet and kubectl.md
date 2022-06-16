# Installing kubeadm, kubelet and kubectl ( for all machine )

You will install these packages on all of your machines:

- `kubeadm`: the command to bootstrap the cluster.
- `kubelet`: the component that runs on all of the machines in your cluster and does things like starting pods and containers.
- `kubectl`: the command line util to talk to your cluster.

kubeadm **will not** install or manage `kubelet` or `kubectl` for you, so you will need to ensure they match the version of the Kubernetes control plane you want kubeadm to install for you.

1. Update the `apt` package index and install packages needed to use the Kubernetes `apt` repository:
    
    ```bash
    sudo apt-get update
    ```
    
    ```bash
    sudo apt-get install -y apt-transport-https ca-certificates curl
    ```
    
2. Download the Google Cloud public signing key:
    
    ```bash
    sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
    ```
    
3. Add the Kubernetes `apt` repository:
    
    ```bash
    echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
    ```
    
4. Update `apt` package index, install kubelet, kubeadm and kubectl, and pin their version:
    
    ```bash
    sudo apt-get update
    ```
    
    ```bash
    # sudo apt-get install -y kubeadm=1.22.6-00 kubelet=1.22.6-00 kubectl=1.22.6-00
    sudo apt-get install -y kubeadm kubelet kubectl
    ```
    
    ```bash
    sudo apt-mark hold kubelet kubeadm kubectl
    ```
    
    > If you want to install the latest version, just omit `ละเลย` the version and run the same line, that will install the latest available. [Releases | Kubernetes](https://kubernetes.io/releases/)
    > 
5. Check kubekdm version
    
    ```bash
    kubeadm version
    ```
