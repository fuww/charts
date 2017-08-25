# Helm Charts

Use this repository for FashionUnited Charts for Kubernetes Helm. Charts are application definitions for Kubernetes Helm. For more information about installing and using Helm, see its
[README.md](https://github.com/kubernetes/helm/tree/master/README.md). To get a quick introduction to Charts see this [chart document](https://github.com/kubernetes/helm/blob/master/docs/charts.md).

## How do I install these charts?

Just `helm install stable/<chart>`. This is the default repository for Helm which is located at https://kubernetes-charts.storage.googleapis.com/ and is installed by default.

For more information on using Helm, refer to the [Helm's documentation](https://github.com/kubernetes/helm#docs).

NOTES:
1. Get the application URL by running these commands:
     NOTE: It may take a few minutes for the LoadBalancer IP to be available.
           You can watch the status of by running 'kubectl get svc 
           -w my-release-webui'
  export SERVICE_IP=$(kubectl get svc --namespace default my-kadira-webui -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
  echo http://$SERVICE_IP:

  NOTES:
1. Get the application URL by running these commands:
     NOTE: It may take a few minutes for the LoadBalancer IP to be available.
           You can watch the status of by running 'kubectl get svc -w my-kadira-webui'
  export SERVICE_IP=$(kubectl get svc --namespace default my-kadira-webui -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
  echo http://$SERVICE_IP: