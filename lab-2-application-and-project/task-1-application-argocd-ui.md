# Task 1 - Application (ArgoCD UI)

1. ArgoCD UI 에서 New APP 을 클릭

<figure><img src="../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>



2. 아래와 같이 설정

* GENERAL&#x20;
  * Application Name : guestbook
  * Project Name : default
* SOURCE
  * Repository URL : https://github.com/argoproj/argocd-example-apps.git
  * Revision : HEAD
  * Path : guestbook
* Destination
  * Cluster URL : https://kubernetes.default.svc
  * Namespace : default

<figure><img src="../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>

3. 입력을 다했다면, <mark style="background-color:red;">상단</mark> CREATE 클릭

<figure><img src="../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>



4. App 생성 화면

<figure><img src="../.gitbook/assets/image (114).png" alt=""><figcaption></figcaption></figure>



5. SYNC 클릭 -> SYNCHRONIZE 클릭

<figure><img src="../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>



6. 상태 확인

<figure><img src="../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>



7. 애플리케이션 클릭

<figure><img src="../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>



8. SVC 클릭

<figure><img src="../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>



9. EDIT 클릭

<figure><img src="../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>



9. type: NodePort 로 변경한 뒤 SAVE 클릭

<figure><img src="../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

10. 변경에 의해 생성된 NodePort Number 확인

<figure><img src="../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>



11. 이전에 확인했던 노드의 IP와 위 10번에서 확인한 NodePort넘버를 활용하여 접속

```
http://<ANY_WORKERNODE_EXTERNALIP>:<GUESTBOOKUI_SERVICE_NODEPORT>
```



<figure><img src="../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>

## <mark style="color:red;">Bug 발생 -> Guestbook 이미지의 문제</mark>&#x20;

## <mark style="color:red;">-> 해당 image 를 nginx 로 수정하여 테스트 구성</mark>



대체구성 1. argo 대시보드의 deployment 클릭

<figure><img src="../.gitbook/assets/image (142).png" alt=""><figcaption></figcaption></figure>

대체구성 2. EDIT 를 클릭하고 image를 nginx 로 수정한뒤 SAVE 클릭

<figure><img src="../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure>







12. Application 으로 구성된 K8S 오브젝트 확인

```
kubectl get all
```

<figure><img src="../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>



13. ArgoCD UI 에서 Application Delete 클릭

<figure><img src="../.gitbook/assets/image (126).png" alt=""><figcaption></figcaption></figure>



14. guestbook 을 입력하고 OK 클릭

<figure><img src="../.gitbook/assets/image (127).png" alt=""><figcaption></figcaption></figure>



15. 삭제 확인

<figure><img src="../.gitbook/assets/image (128).png" alt=""><figcaption></figcaption></figure>

```
kubectl get all
```

<figure><img src="../.gitbook/assets/image (129).png" alt=""><figcaption></figcaption></figure>
