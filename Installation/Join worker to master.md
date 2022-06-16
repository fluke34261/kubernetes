# Join worker to master ( only worker machine )

1. Change instant name
    
    ```bash
    sudo hostnamectl set-hostname worker-node1
    ```
    
2. Reset kubeadm
    
    > [preflight] Running pre-flight checks
    error execution phase preflight: [preflight] Some fatal errors occurred:
    [ERROR FileAvailable--etc-kubernetes-pki-ca.crt]: /etc/kubernetes/pki/ca.crt already exists
    [preflight] If you know what you are doing, you can make a check non-fatal with `--ignore-preflight-errors=...`
    To see the stack trace of this error execute with --v=5 or higher
    > 
    
    ```bash
    sudo kubeadm reset
    ```
    
3. Initial kubeadm worker
    
    ```bash
    sudo kubeadm join 192.168.1.101:6443 --token 9y1tw0.j0rhtjmh6sj75bp9 --discovery-token-ca-cert-hash sha256:4d4d48dcb0ceab63f0da74e00be7a29cf720ff2b0ca9c7208a7b1df36433f6bc
    ```
