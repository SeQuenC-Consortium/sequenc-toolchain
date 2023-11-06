Run using kubernetes / minikube
=========================================

1. Start Docker (e.g. Docker Desktop)
2. Start minikube


```bash
    minikube start
```

3. Set minikube as docker env
    Minkube needs to be set as docker environment to be able to build images for minikube. Otherwise Minikube would not
    be able to find the images. This needs to be done every time a new terminal is opened.
    !!In this version if not modified, the image is pulled from dockerhub to facilitate the usage

```bash
    minikube docker-env | Invoke-Expression
```

4. Start services and pods with configuration
    If the directory containing all the service and deployment files is named minikube, start it with the following command:

```bash
    kubectl apply -f minikube
```

5. Expose qunicorn through minikube (start in another terminal)
    Exposes the qunicorn service to the internet. This is needed to be able to access the service from outside the cluster.

```bash
    minikube tunnel
```

6. List service information using

```bash
    kubectl get svc
```

7. Get existing pos and fill database with data

```bash
    kubectl get po --selector=io.kompose.service=server

    kubectl exec {name of server pod}  -- python -m flask create-and-load-db
```

8. Now you can access qunicorn using [EXTERNAL-IP]:8080/swagger-ui of the server service


Other useful commands
----------------------

* Clear all kubectl pods and services

```bash
    kubectl delete daemonsets,replicasets,services,deployments,pods,rc,ingress --all --all-namespaces
```

* Expose service and create Tunnel

```bash
    minikube service {service}
```


---

## Notes

 - The keycloak container might crash at the moment
 - Workflow Modeler not in the cluster yet
 - QC-Atlas not in the cluster yet
 - TODO: Port of server is 8080, change to 5005 after adding more components
 - Database should be filled with 5 deployments and 3 jobs without the command in this setup