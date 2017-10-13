# helm-charts
My public helm chart repository

## Usage

```shell-session
$ helm repo add koudaiii https://koudaiii.github.io/helm-charts
"koudaiii" has been added to your repositories

$ helm repo update
Hang tight while we grab the latest from your chart repositories...
...Skip local chart repository
...Successfully got an update from the "incubator" chart repository
...Successfully got an update from the "stable" chart repository
...Successfully got an update from the "koudaiii" chart repository
Update Complete. ⎈ Happy Helming!⎈

$ helm search koudaiii
NAME                  	VERSION	DESCRIPTION
koudaiii/sample-go-api	0.1.0  	A Helm chart for Kubernetes
```

## Deploy to Minikube

```shell-session
$ helm install --name my-helm-chart --set service.type=NodePort koudaiii/sample-go-api
NAME:   my-helm-chart
LAST DEPLOYED: Sat Oct 14 05:26:39 2017
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1beta1/Deployment
NAME                         DESIRED  CURRENT  UP-TO-DATE  AVAILABLE  AGE
my-helm-chart-postgresql     1        1        1           0          1s
my-helm-chart-sample-go-api  1        1        1           0          1s

==> v1/Secret
NAME                         TYPE    DATA  AGE
my-helm-chart-postgresql     Opaque  1     1s
my-helm-chart-sample-go-api  Opaque  1     1s

==> v1/PersistentVolumeClaim
NAME                      STATUS  VOLUME                                    CAPACITY  ACCESSMODES  STORAGECLASS  AGE
my-helm-chart-postgresql  Bound   pvc-d1e58b41-b054-11e7-98ef-080027e29533  10Gi      RWO          standard      1s

==> v1/Service
NAME                         CLUSTER-IP  EXTERNAL-IP  PORT(S)       AGE
my-helm-chart-postgresql     10.0.0.89   <none>       5432/TCP      1s
my-helm-chart-sample-go-api  10.0.0.135  <nodes>      80:30986/TCP  1s


NOTES:
1. Get the application URL by running these commands:
  export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services my-helm-chart-sample-go-api)
  export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
  echo http://$NODE_IP:$NODE_PORT
```

## Development

Clone this repository and add `chart`.

```shell-session
$ git clone https://github.com/koudaiii/helm-charts
$ cd helm-charts
$ mkdir sample-chart
$ script/build
```

## Contribution

1. Fork ([https://github.com/koudaiii/helm-charts/fork](https://github.com/koudaiii/helm-charts/fork))
1. Create a feature branch
1. Commit your changes
1. Rebase your local changes against the master branch
1. Create a new Pull Request

## Author

[koudaiii](https://github.com/koudaiii)

## License

[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)
