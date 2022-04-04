# Devops-zadanie

---

### Vybral som Option 2
#### The Task
##### Your task is to create a repo in github and solve below problem
**1.** Create a new namepace in kubernetes and deploy all solution in that namespace

**2.** Create a kubernetes deployment, svc, hpa, pdb service account in kubernetes cluster. can be
PaaS/Minikube
**3.** Deployment needs an API_KEY which is a secret key. Mount this API_KEY as volume inside
Deployment
**4.** Create a kubernetes role binding so that this secret is readable only from this namespace
**5.** e.g. namespace ns1 users can access secret s1 but namespace ns2 apps/users can not access
secret s1

##### Acceptance criteria
You must provide your code in full with kubernetes manifests or pipelines or scripts
You must use either public cloud(AWS, GCP, Azure) or Minikube to run the above manifests file
You do not need to provide access to the cluster in public cloud, only the code
Your code is clean and readable
You must document any steps that are not automated in the README.md
You must have dedicated service account for deployment
You must have NodePort Type of service for application
You must have Minimum 2 pods always up and running
You must have only 1 pod unavailable during Rolling Update of Deployment
##### Assumptions
**1.** Can use any open-source tools/language to solve problem
**2.** Create extra code if needed like infra(terraform, scripts) etc in same repo
**3.** Choose simple applications from internet e.g. nginx, httpd
##### Bonus
**1.** Deployment container is scanned before getting deployed. If severity is high, pipeline should fail
**2.** Container in Pod, should not be running as root
**3.** Scan app repo code to see static code anyalysis in pipeline

---

### Not automated steps

Vytvorenie namespacu a prepnutie na namespace **ns1**
```
$ kubectl create namespace ns1
$ kubens ns1
```

---

Deploy všetkych resource files do minikube cluster
```
$ kubectl apply -f secret.yaml
$ kubectl apply -f app-hpa.yaml
$ kubectl apply -f app-pdb.yaml
$ kubectl apply -f serviceaccount.yaml
$ kubectl apply -f deployment.yaml
```

---

Kontrola či sa dobre vytvorili všetky komponenty v clusteri
```
$ Kubectl get all
```

Zistenie minikube ip adresy a nasledne pozretie appky na localhoste (minikubeIP:NodePort)
```
$ minikube ip
```

✌🏽
