# Explication des Name Spaces
## **Development :**
Le namespace **development** est celui qui stock l'état d'avancement avant de le passer en "production".

## **BDD :**
Le namespace **BDD** est celui qui stock toutes les données.

## **Production :**
Mise en **production** des éléments développé dans le namspace **development**.



## Pour creer les namespaces
kubectl apply -f namespaces.yaml


## Pour creer les resourcequotas
kubectl apply -f quotas.yaml 


## Pour creer le configmap 
kubectl get configmap configmap-wordpress 