# Task 2 - Repository 연동 (Github - ArgoCD)

1. ArgoCD UI 에서 Settings 클릭, Repositories 클릭

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>



2. CONNECT REPO 클릭&#x20;

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>



3. VIA HTTPS 선택

<figure><img src="../.gitbook/assets/image (16).png" alt="" width="391"><figcaption></figcaption></figure>



4. 아래와 같이 입력후 상단 CONNECT 클릭

* Type: git
* Project : default
* Repo URL : https://github.com/\<GITHUB USERNAME>/myrepo.git

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>



5. 연동 확인

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>



6. Task 1 - Repository 연동 (Github-C9) 작업에서 업로드했던 yaml 파일 기반으로 ArgoCD Application 생성

```
argocd app create sampleapp \
--repo https://github.com/<GITHUB USERNAME>/myrepo.git \
--path . \
--dest-server https://kubernetes.default.svc \
--dest-namespace default
```

<figure><img src="../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>



7. 동기화&#x20;

```
argocd app sync sampleapp
```
