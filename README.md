# Damn Vulnerable Web Application (DVWA) on k8s

1. create namespce.

```
kubectl create ns dvwa
```

2. create Deployment and Service LoadBalancer.

```
kubectl -n dvwa apply -f dvwa.yml
```

3. check resource status.

```
kubectl -n dvwa get all
```

4. get address and port.

default login: admin / password

```
$ kubectl -n dvwa get service dvwa-svc
NAME       TYPE           CLUSTER-IP     EXTERNAL-IP     PORT(S)        AGE
dvwa-svc   LoadBalancer   100.65.209.4   192.168.24.19   80:30686/TCP   9m26s
$ kubectl -n dvwa get service dvwa-svc -o jsonpath='{.status.loadBalancer.ingress[].ip}:{.spec.ports[0].port}' | more
192.168.24.19:80
```

5. delete dvwa.

```
kubectl delete ns dvwa
```

