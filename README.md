# Explication des Name Spaces
## **Development :**
Le namespace **development** est celui qui stock l'état d'avancement avant de le passer en **production.**

## **BDD :**
Le namespace **BDD** est celui qui stock toutes les données.

## **Production :**
Mise en **production** des éléments développé dans le namspace **development.**

## Start the cluster and scale:

**kubectl create secret generic mysql-pass --from-literal=password=YOUR_PASSWORD**
kubectl get secrets (optionnel)
**kubectl create -f wordpress/mysql-deployment.yaml**
**kubectl create -f wordpress/wordpress-deployment.yaml**
kubectl get pv (optionnel)
kubectl get pvc (optionnel)
kubectl get pods (optionnel)
kubectl get services (optionnel)
**minikube service wordpress --url**
**kubectl create -f wordpress/wordpress-htaccess-configmap.yaml**

## Scale Wordpress and mysql:
kubectl scale --replicas X deployments wordpress-mysql
kubectl scale --replicas X deployments wordpress

## Cleanup
kubectl delete secret mysql-pass
kubectl delete deployment -l app=wordpress
kubectl delete service -l app=wordpress
kubectl delete pvc -l app=wordpress
kubectl delete pv -l app=wordpress
minikube stop


## Installer Prometheus et Grafana 
kubectl apply --filename https://raw.githubusercontent.com/giantswarm/prometheus/master/manifests-all.yaml
kubectl get pods,svc,replicaset,deploy -n monitoring (optionnel)
kubectl port-forward --namespace monitoring service/grafana 3000:3000


// MODE DEV 

kubectl create secret generic mysql-pass --from-literal=password=YOUR_PASSWORD
kubectl create -f mysql-deployment.yaml
kubectl create -f wordpress-deployment.yaml
kubectl create -f wordpress-htaccess-configmap.yaml
minikube service wordpress --url

kubectl delete secret mysql-pass
kubectl delete configmap wordpress-php-options
kubectl delete deployment -l app=wordpress
kubectl delete service -l app=wordpress
kubectl delete pvc -l app=wordpress
kubectl delete pv -l app=wordpress