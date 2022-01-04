# Explication des Name Spaces
## **Development :**
Le namespace **development** est celui qui stock l'état d'avancement avant de le passer en **production.**

## **BDD :**
Le namespace **BDD** est celui qui stock toutes les données.

## **Production :**
Mise en **production** des éléments développé dans le namspace **development.**

## Pour creer les namespaces
kubectl apply -f namespaces.yaml

## Pour creer les resourcequotas
kubectl apply -f quotas.yaml 

## Pour creer le configmap 
kubectl get configmap configmap-wordpress

## Create MySQL Portworx PersistentVolume(PV) and PersistentVolumeClaim(PVC)
kubectl apply -f mysql-vol.yaml
kubectl apply -f wordpress-vol.yaml
kubectl create secret generic mysql-pass --from-file=password.txt
kubectl create -f mysql.yaml
kubectl create -f wordpress-deployment.yaml