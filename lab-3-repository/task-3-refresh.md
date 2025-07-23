# Task 3 - Refresh

1. Service 생성하는 yaml 생성

```
cat <<EOF > sample-svc.yaml
apiVersion: v1
kind: Service
metadata:
  name: sample-svc
  namespace: default
spec:
  selector:
    app: sample-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
EOF
```



2. 파일 목록확인

```
ls
```



3. git push 로 repo에 업로드

```
git add .
git commit -m "svc update"
git push -u origin main
```



4. Git Repo 에는 파일이 푸시 되었으나, ArgoCD 에서는 변화가 없음을 확인

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

&#x20;

<figure><img src="../.gitbook/assets/image (47).png" alt="" width="563"><figcaption></figcaption></figure>



5. 최대 3분이 지나야 Refresh 가 되어 GIT 저장소의 변화를 ArgoCD 가 인지

<figure><img src="../.gitbook/assets/image (49).png" alt="" width="563"><figcaption></figcaption></figure>

6. sync를 클릭, SYNCHRONIZE 를 클릭하여 k8s 적용

<figure><img src="../.gitbook/assets/image (51).png" alt="" width="563"><figcaption></figcaption></figure>



7. Refresh 주기를  짧게 설정하기 위해 Configmap에 변수 추가

```
kubectl -n argocd edit configmap argocd-cm
```

```
data:
  timeout.reconciliation: "60"
```

<figure><img src="../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>



8. 변경사항 저장후 ArgoCD 재시작

```
kubectl rollout restart deployment argocd-server -n argocd
```



9. 이번에는 deploy yaml의 내용을 수정

```
vi sample-dp.yaml
```

```
replicas: 5
```

<figure><img src="../.gitbook/assets/image (53).png" alt="" width="333"><figcaption></figcaption></figure>

10. git push

```
git add .
git commit -m "replicas update"
git push -u origin main
```



11. 최대 1분 뒤 Refresh 가 되어 GIT 저장소의 변화를 ArgoCD 가 인지

<figure><img src="../.gitbook/assets/image (54).png" alt="" width="563"><figcaption></figcaption></figure>



12. sync를 클릭, SYNCHRONIZE 를 클릭하여 k8s 적용

