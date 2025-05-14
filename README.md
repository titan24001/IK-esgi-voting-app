# Voting App sur Kubernetes avec Minikube --- ESGI - Indrit KULLA 5SRC2



## Objectif du Projet

L'objectf de ce projet de mise en œuvre de l’application open-source Example Voting App https://github.com/dockersamples/example-voting-app dans un cluster Minikube.

## Prérequis
Les outils suivants doivent être installés: 
- docker
- Kubectl
- Minikube 
- Git 

## Architecture de l’Application
![image](https://github.com/user-attachments/assets/c65086ac-9607-4181-9f10-6f4046b09950)

## I - Clonage du Dépôt

```shell
git clone git@github.com:titan24001/IK-esgi-voting-app.git
cd IK-esgi-voting-app/
```

## II -Déploiement Kubernetes


### 1.  Démarrer Minikube 
```shell
minikube start --driver=docker
```

### 2.  Appliquer les fichiers Kubernetes

```shell
kubectl apply -f k8s-specifications/
```

## III -Vérification du Déploiement


### 1.  Vérifier que tous les Pods sont en fonctionnement

```shell
kubectl get pods
```

![image](https://github.com/user-attachments/assets/b5b2b08d-87f8-4b4c-827f-7c475477fae7)

### 2. Vérifier les services

```shell
kubectl get svc
```

![image](https://github.com/user-attachments/assets/f99d1436-c0af-4e21-8131-6a8380f2e7a4)

Une fois que tous les pods soient en Running ou Completed.

### 3. Utilisez Minikube pour exposer les services externes :

```shell
minikube service vote
minikube service result
```
![image](https://github.com/user-attachments/assets/ed5ae339-8b65-4b71-9f9b-e974baa278ed)

### 4. Pourexposer les services à la machine physique il faut faire un tunnel SSH :

```shell
ssh -L 31000:192.168.49.2:31000 -L 31001:192.168.49.2:31001 user@ipdelamachine
```

## IV -Accéder à l'application

###  Interface de vote
Accédez à l’interface de vote via le navigateur à l’adresse suivante : (http://localhost:31000)
![image](https://github.com/user-attachments/assets/6bc7676d-ebb0-43b2-8835-502e12496ec4)

### Test de noter 
![image](https://github.com/user-attachments/assets/a60691e4-b8c4-4817-87e0-a11615eda572)


###  Interface de résultat
Pour consulter les résultats allez sur : (http://localhost:31001)
![image](https://github.com/user-attachments/assets/6ee5701c-173f-4bed-bbd5-841bcc8a2c0f)

