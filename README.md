# Explication des Name Spaces
## **Development :**
Le namespace **development** est celui qui stock l'état d'avancement avant de le passer en **production.**

## **BDD :**
Le namespace **BDD** est celui qui stock toutes les données.

## **Production :**
Mise en **production** des éléments développé dans le namspace **development.**


## **Start minikube :**
**minikube delete**
**minikube start --kubernetes-version=v1.20.0 --memory=6g --bootstrapper=kubeadm --extra-config=kubelet.authentication-token-webhook=true --extra-config=kubelet.authorization-mode=Webhook --extra-config=scheduler.bind-address=0.0.0.0 --extra-config=controller-manager.bind-address=0.0.0.0**
**minikube addons disable metrics-server**

## **Init wordpress :**
**kubectl create secret generic mysql-pass --from-literal=password=YOUR_PASSWORD**
**kubectl create -f ./wordpress/mysql-deployment.yaml**
**kubectl create -f ./wordpress/wordpress-deployment.yaml**
**kubectl create -f ./wordpress/wordpress-htaccess-configmap.yaml**
**kubectl create -f ./wordpress/nginx-ingress.yaml**
**minikube service wordpress --url**

## **Scale Wordpress and mysql:**
**kubectl scale --replicas X deployments wordpress-mysql**
**kubectl scale --replicas X deployments wordpress**

## **Installer prometheus + node-exporter + grafana**
**kubectl apply --filename https://raw.githubusercontent.com/giantswarm/prometheus/master/manifests-all.yaml**
**kubectl get pods,svc,replicaset,deploy -n monitoring (optionnel)**
**kubectl port-forward --namespace monitoring service/grafana 3000:3000**
Se connecter avec :
**id:** admin
**mdp:** admin


## **Prometheus :**
**kubectl --namespace monitoring port-forward svc/prometheus-k8s 9090**

## **Graphana :**
**kubectl --namespace monitoring port-forward svc/grafana 3000**

// RBAC tests :
**minikube start --extra-config=apiserver.Authorization.Mode=RBAC**


## **Cleanup**
**kubectl delete secret mysql-pass**
**kubectl delete configmap wordpress-php-options**
**kubectl delete deployment -l app=wordpress**
**kubectl delete service -l app=wordpress**
**kubectl delete pvc -l app=wordpress**
**kubectl delete -f ./wordpress/nginx-ingress.yaml**
**kubectl delete pv -l app=wordpress**
**kubectl delete --ignore-not-found=true -f manifests/ -f manifests/setup**
