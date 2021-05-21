## Docker ASP.NET Core Sample

Open the solution in Visual Studio, set "docker-compose" as start project and run.

To run from CLI, use `docker-compose build` and then `docker-compose up`. Navigate to `http://localhost:5902/` from the browser.

## Local Kubernetes deployment (without local code build)

The deploy scripts by default uses the images from my DockerHub. Local building of the images aren't required if you are only testing the application in k8s.

Navigate to k8s folder and apply both the deployments to K8S.

 `kubectl apply -f .\deploy-backend.yaml`

 `kubectl apply -f .\deploy-frontend.yaml`


Use the following command to check if the pods are running successfully:

`kubectl get po`

Make sure the containers are running:

```
➜  k8s git:(main) ✗ kubectl get po
NAME                        READY   STATUS    RESTARTS   AGE
backend-5b7b5b4855-dtlhw    1/1     Running   0          4m32s
frontend-5f7fdfdb77-ngxfk   1/1     Running   0          4m25s
➜  k8s git:(main) ✗
```

Map a local port and navigate to the local url:

```
kubectl port-forward svc/frontend 5600:80
```
Navigate to `http://localhost:5600` in a browser to verify the app.
