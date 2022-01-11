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
**kubectl create -f mysql-deployment.yaml**
**kubectl create -f wordpress-deployment.yaml**
kubectl get pv (optionnel)
kubectl get pvc (optionnel)
kubectl get pods (optionnel)
kubectl get services (optionnel)
**minikube service wordpress --url**

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