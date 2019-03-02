# Postgresql DigitalOcean Kubernetes 
Run postgresql in DigitalOcean Kubernetes with persistent volume claim


## Prerequisites
1. Digitalocean kubernetes cluster since we run this configuration on DigitalOcean environment, GCP and other resource will come in next repository
2. Make sure your kubectl already installed
3. Download the kubernetes_config.yaml from DigitalOcean this config file rotated every week


## How to
1. Make sure you have access to your clusters
   ```bash
    kubectl --kubeconfig="path_to_your_kubeconfig.yaml" get nodes
    ```

    It will list of all your kubernetes cluster's nodes

2. Setup Digitalocean PVC visit this documentation for more information
   [CSI DigitalOcean](https://github.com/digitalocean/csi-digitalocean)

3. Create Kubernetes Persistent Volume
   ```bash
    kubectl --kubeconfig="path_to_your_kubeconfig.yaml" create -f pvc.yaml
    ```

4. Check if your persisten volume claim success
   ```bash
   kubectl --kubeconfig="path_to_your_kubeconfig.yaml" get pv
    ```

5. Create postgres deployment
   ```bash
    kubectl --kubeconfig="path_to_your_kubeconfig.yaml" create -f postgres.yaml
    ```
    This process may take few mintes

    Check deployment status
    ```bash
    kubectl --kubeconfig="path_to_your_kubeconfig.yaml" get deployments
    ```

    Check your service status
    ```bash
    kubectl --kubeconfig="path_to_your_kubeconfig.yaml" get service
    ```

7. Finished! Now you can access your postgres throug external ip address in Service and his port
   For example: 192.xxx.xx:5432 and use postgres credentials that we set up through configmap.yaml

8. Support by star this repository ;)