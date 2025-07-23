# Task 2 - Web UI 접속 및 암호설정



1. 서비스 유형 변경&#x20;

```
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'
```



2. &#x20;노드포트 넘버 확인

```
kubectl get svc argocd-server -n argocd
```

<figure><img src="../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>



3. 워커노드의  터미널에서External IP 확인

```
curl ifconfig.io
```



4. 위에서  3번에서 확인한 워커노드 External IP와, 2번에서 확인한 노드포트를 활용하여 웹브라우저에 접속

```
http://<ANY_WORKERNODE_EXTERNALIP>:<ARGOCDSERVER_SERVICE_NODEPORT>
```



5. 크롬 브라우저 기준 ->  고급 클릭 -> 안전하지 않음 클릭

<figure><img src="../.gitbook/assets/image (99).png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (102).png" alt="" width="563"><figcaption></figcaption></figure>



6. 로그인 페이지 확인

<figure><img src="../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>



7. 암호 확인&#x20;

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```



8. 대시보드 로그인

<mark style="background-color:blue;">Username : admin</mark>&#x20;

<mark style="background-color:blue;">Password : 7에서 확인한 암호</mark>



9. 로그인 성공 화면

<figure><img src="../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>



10. 터미널에서 argocd login

```
argocd login <ANY_WORKERNODE_EXTERNALIP>:<ARGOCDSERVER_SERVICE_NODEPORT> --insecure
```
<mark style="background-color:blue;">Username : admin</mark>&#x20;

<mark style="background-color:blue;">Password : 7에서 확인한 암호</mark>

<figure><img src="../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>



11. 암호변경 (실습환경이기 때문에 변경할 패스워드는 argocd!23 으로 지정)

```
argocd account update-password
```

<figure><img src="../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>



12. 비밀번호를 변경했다면, 기존 초기 패스워드를 갖고있는 Secret 삭제

```
kubectl delete secret -n argocd argocd-initial-admin-secret
```

<figure><img src="../.gitbook/assets/image (108).png" alt=""><figcaption></figcaption></figure>
