# Task 1 - ArgoCD, ArgoCD CLI 설치

1. 네임스페이스 생성&#x20;

```
kubectl create ns argocd
```



2. ArgoCD 설치

```
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```


3. 설치 확인

```
kubectl get pod -n argocd
```

<figure><img src="../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>



4. 그외 구성되는 내용 확인

```
kubectl get all -n argocd
```



5. curl 을 이용하여 최신버전의 ArgoCD Cli다운로드

```
curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
```



6. ArgoCD Cli 설치

```
sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
rm argocd-linux-amd64
```



7. 설치 및 버전확인 (FATA 메시지는 Task2 를 완료하게되면 해결)

```
argocd version
```

<figure><img src="../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>
