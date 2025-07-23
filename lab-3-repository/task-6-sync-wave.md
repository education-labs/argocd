# Task 6 - Sync Wave

1. git 디렉토리의 yaml 삭제&#x20;

```
ls
rm sample-dp.yaml
```



2. ns, deploy, svc yaml 생성

```
cat <<EOF > wave-ns.yaml
apiVersion: v1
kind: Namespace
metadata:
  name: syncwave-namespace
  annotations:
    argocd.argoproj.io/sync-wave: "0"
EOF
```

```
cat <<EOF > wave-deploy.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: syncwave-app
  namespace: syncwave-namespace
  annotations:
    argocd.argoproj.io/sync-wave: "1"
spec:
  replicas: 1
  selector:
    matchLabels:
      app: syncwave-app
  template:
    metadata:
      labels:
        app: syncwave-app
    spec:
      containers:
      - name: supermario
        image: pengbai/docker-supermario
        ports:
        - containerPort: 8080
EOF
```

```
cat <<EOF > wave-svc.yaml
apiVersion: v1
kind: Service
metadata:
  name: syncwave-service
  namespace: syncwave-namespace
  annotations:
    argocd.argoproj.io/sync-wave: "2"
spec:
  selector:
    app: syncwave-app
  ports:
    - protocol: TCP
      port: 8080
      targetPort: 8080
      nodePort: 30080
  type: NodePort
EOF
```



3. 생성확인

```
ls
```

<figure><img src="../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>



4. git push

```
git add .
git commit -m "wave push"
git push -u origin main
```





5. ArgoCD에서 Refresh 를 한 뒤 생성 순서 확인



6. 아래명령을 이용하여 ip 확인 및 서비스의 노드포트 확인

```
curl ifconfig.io
kubectl get svc -n syncwave-namespace
```

<figure><img src="../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>



7. 웹브라우저에서 해당 아이피와 포트로 접속

```
IP:PORT
```

