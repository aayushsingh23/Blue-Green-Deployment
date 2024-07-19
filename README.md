
# Blue-Green Deployments
In the modern world of software development, deploying new versions of applications is a crucial part of the development cycle. However, rolling out updates to production environments can be a risky proposition, as even small issues can result in significant downtime and lost revenue. Blue-Green Deployments are a deployment strategy that mitigates this risk by ensuring that new versions of applications can be deployed with zero downtime.

## Deploying pods and services
Deploy blue deployement

```bash
    kubectl apply -f blue-app.yaml
```

THis has an HTML file which will be served.

Create Service, this is which will deploy the deployments

```bash
    kubectl apply -f service.yaml
```
This will serve the blue deployment.

Deploy green environment

```bash
    kubectl apply -f green-app.yaml
```

To test green environment make a temporary green service.

```bash
    kubectl apply -f green-service.yaml
```

You can test this by accessing the service.

```bash
    kubectl port-forward svc/my-app-green-service 8080:8080
```

Once the changes have been made you can switch the traffic to green deployment.

Change the `version` in `service.yaml` file from `blue` to `green`.
Then apply the changes.

```bash
    kubectl apply -f service.yaml
```

For cleanup delete the blue deployment

```bash
    kubectl delete deployment my-app-blue
```
## Documentation

[Kubernetes](https://kubernetes.io/docs/home/)

[Minikube](https://minikube.sigs.k8s.io/docs/)

[Blue-Green-Deployments](https://medium.com/cloud-native-daily/blue-green-deployments-with-kubernetes-a-comprehensive-guide-5d196dad1976)


