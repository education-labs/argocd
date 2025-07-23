# Task 2 - Application (CMD 구성)

1. kubectl 의 현재 네임스페이스를 argocd 로 변경

```
kubectl config set-context --current --namespace=argocd
```

<figure><img src="../.gitbook/assets/image (132).png" alt=""><figcaption></figcaption></figure>



2. Task 1 에서 구성한 Application을 argocd cli 명령어로 구성

```
argocd app create guestbook \
--repo https://github.com/argoproj/argocd-example-apps.git \
--path guestbook \
--dest-server https://kubernetes.default.svc \
--dest-namespace default
```

<figure><img src="../.gitbook/assets/image (131).png" alt=""><figcaption></figcaption></figure>



3. 배포된 내용 확인

```
kubectl get all -n default
```

<figure><img src="../.gitbook/assets/image (133).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (134).png" alt=""><figcaption></figcaption></figure>

4. Application 확인

```
argocd app get guestbook
```

<figure><img src="../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>



5. 동기화 실행, 다시 APP 확인

```
argocd app sync guestbook
```

```
argocd app get guestbook
```

<figure><img src="../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>



6. 생성된 k8s 오브젝트 확인&#x20;

```
kubectl get all -n default
```

<figure><img src="../.gitbook/assets/image (139).png" alt=""><figcaption></figcaption></figure>



7. Application 삭제

```
argocd app delete guestbook

y
```

<figure><img src="../.gitbook/assets/image (140).png" alt=""><figcaption></figcaption></figure>



8. 삭제되었는지 확인

```
argocd app list
```

```
kubectl get all -n default
```

<figure><img src="../.gitbook/assets/image (141).png" alt=""><figcaption></figcaption></figure>



9. 기본 네임스페이스 타겟 설정 복구

```
kubectl config set-context --current --namespace=default
```
