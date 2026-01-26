run cmd as administrator
minikube start --driver=hyperv

docker build -t kube-first-app .
docker tag kube-first-all berkerturan/kube-first-app

docker build -t berkerturan/kube-first-app .
docker push berkerturan/kube-first-app
kubectl create deployment first-app --image=kube-first-app

kubectl get deployment
kubectl get pods

kubectl expose deployment first-app --type=LoadBalancer --port=8080

minikube service first-app

kubectl scale deployment/first-app --replicas=3 -->birden çok pod yaratmak için

kubectl set image deployment/first-app kube-first-app=berkerturan/kube-first-app:1 -->güncel image ı çekmek için

kubectl rollout status deployment/first-app -->deployment statusunu takip etmek için

kubectl rollout undo deployment/first-app -->rollback yapmak için

kubectl rollout history deployment/first-app -->Tüm deployment revizyonlarını görmek için

kubectl rollout history deployment/first-app --revision=3  --> Revizyon detayını görmek için

kubectl rollout undo deployment/first-app --to-revision=5 -->spesific revision a gönmek için

kubectl delete service first-app 
kubectl delete deployment first-app 


---DECLERATIVE APPROACT---
minicube start --driver=hyperv

kubectl apply -f deployment.yml
kubectl apply -f service.yml

kubectl get services komutu ile servisleri alırsın
servis de Loadbalancer olan servis'in adını 
minikube start <nameOfService> ---> 