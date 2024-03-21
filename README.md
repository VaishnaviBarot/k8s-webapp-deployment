Task 1:
sudo systemctl start docker
docker ps
kubectl get all -n kube-system
kubectl describe pod/kube-apiserver-kind-control-plane 
kubectl get all -n webapp-namespace
kubectl get all -n mysql-namespace

Task2 :

kubectl apply -f mysql-pod.yaml -n mysql-namespace
kubectl describe pod sql-pod -n mysql-namespace
kubectl apply -f app-pod.yaml -n webapp-namespace
kubectl port-forward web-app-pod 8080:8080 -n webapp-namepace
curl localhost:8080
kubectl logs sql-pod -n mysql-namespace
kubectl logs web-app-pod -n webapp-namespace

Task 3
kubectl apply -f mysql-replicasets.yaml -n mysql-namespace 
kubectl apply -f app-replicasets.yaml -n webapp-namespace 

Task 4
kubectl apply -f mysql-deployment.yaml -n mysql-namespace 
kubectl apply -f webapp-deployment.yaml -n webapp-namespace 


Task5
kubectl apply -f mysql-service.yaml -n mysql-namespace 
kubectl apply -f app-service.yaml -n webapp-namespace 



kubectl describe pod sql-pod -n mysql-namespace

kubectl describe replicaset web-app-replicaset -n webapp-namespace    

kubectl describe pod web-app-pod -n webapp-namespace

kubectl delete pod sql-pod -n mysql-namespace

kubectl port-forward web-app-pod 8080:8080 -n webapp-namepace

           


10.244.0.6