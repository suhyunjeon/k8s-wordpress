# k8s-wordpress
Minikube VM을 사용하여 local에 kubernetest를 spin up합니다. 
이 소스코드는 k8s기반 wordpress 구축 예제입니다. 

# Getting Started
minikube 시작  
```
$ minikube start --driver=docker
```

kubernetest pod 전체 확인  
```
$ kubectl get pods --all-namespaces

NAMESPACE     NAME                               READY   STATUS    RESTARTS       AGE
kube-system   coredns-5dd5756b68-gbnw5           1/1     Running   0              3h5m
kube-system   etcd-minikube                      1/1     Running   0              3h5m
kube-system   kube-apiserver-minikube            1/1     Running   0              3h6m
kube-system   kube-controller-manager-minikube   1/1     Running   0              3h5m
kube-system   kube-proxy-s9vzj                   1/1     Running   0              3h5m
kube-system   kube-scheduler-minikube            1/1     Running   0              3h6m
kube-system   storage-provisioner                1/1     Running   0              3h5m
```

YAML file 실행  
```
$ kubectl apply -f ./
secret/mysql-pass-df44tkf8t9 created
service/wordpress created
service/wordpress-mysql created
persistentvolumeclaim/mysql-pv-claim created
persistentvolumeclaim/wp-pv-claim created
deployment.apps/wordpress created
deployment.apps/wordpress-mysql created
```

Dedployments 확인   
```
$ kubectl get pods; kubectl get pvc; kubectl get secret; kubectl get deployments
```

Wordpress 접근  
```
$ minikube service wordpress
|-----------|-----------|-------------|---------------------------|
| NAMESPACE |   NAME    | TARGET PORT |            URL            |
|-----------|-----------|-------------|---------------------------|
| default   | wordpress |          80 | http://192.168.49.2:31251 |
|-----------|-----------|-------------|---------------------------|
🎉  Opening service default/wordpress in default browser...
👉  http://192.168.49.2:31251
```
