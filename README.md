# Wordpress, MySQL And Persistent Volumes

 Deploying WordPress and MySQL using PersistentVolumes and PersistentVolumeClaims.  
 This tutorial is geared towards setting up a simple WordPress site and MySQL database on a Kubernetes cluster, ideal for testing but not suitable for production.  

Here's a brief outline of the key steps:

1. **Set Up Your Cluster**: 
   - Make sure you have a Kubernetes cluster running, and `kubectl` is configured. You can use Minikube for local testing or other Kubernetes playgrounds.
   
2. **Persistent Volumes and Claims**:
   - WordPress and MySQL both need PersistentVolumes (PVs) for data storage, which will be managed through PersistentVolumeClaims (PVCs). If your cluster has a default `StorageClass`, it will automatically handle provisioning PVs based on your PVCs.

3. **Configuration Files**:
   - Download the configuration files for MySQL (`mysql-deployment.yaml`) and WordPress (`wordpress-deployment.yaml`).
   - Create a `kustomization.yaml` file to manage resources and secrets using `kubectl`. This file will contain configurations for generating a MySQL password secret, as well as linking the MySQL and WordPress deployments.

4. **Deploying MySQL and WordPress**:
   - Deploy both MySQL and WordPress by applying the `kustomization.yaml` using `kubectl apply -k ./`.
   - Verify the existence of the `Secrets`, `PersistentVolumes`, and `Pods` to ensure they are running as expected.

5. **Access WordPress**:
   - Use the `minikube service wordpress --url` command to get the URL to access WordPress. Open the URL in a browser to set up the WordPress site.

6. **Cleaning Up**:
   - Once you're done, clean up the resources by running `kubectl delete -k ./`.
  
 7. **Commands lines**:
    ```
    $ minikube start  
    $ git clone https://github.com/sialorama/wordpress_mysql_persistentvolumes.git
    $ cd wordpress_mysql_persistentvolumes
    $ kubectl apply -k ./
    $ kubectl get secrets
    $ kubectl get pvc
    $ kubectl get po
    $ kubectl get service wordpress
    $ minikube service wordpress --url
    ```

