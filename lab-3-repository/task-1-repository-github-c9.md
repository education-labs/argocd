# Task 1 - Repository 연동 (Github-C9)

1. Github 계정 생성

```
https://github.com
```

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>



2. 계정이 있다면 로그인



3. 상단 Repositories를 클릭, 우측 New 클릭&#x20;

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>



4. Repository 이름에 myrepo 라고 입력한 뒤 Create 버튼 클릭

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

6. 우측 상단의 계정 아이콘 클릭

<figure><img src="../.gitbook/assets/image (18).png" alt="" width="563"><figcaption></figcaption></figure>



7. Settings 클릭

<figure><img src="../.gitbook/assets/image (19).png" alt="" width="232"><figcaption></figcaption></figure>



8. 좌측 하단에 Developer settings 클릭, Personal access tokens 클릭, Tokens(classic) 클릭

<figure><img src="../.gitbook/assets/image (20).png" alt="" width="294"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (67).png" alt="" width="262"><figcaption></figcaption></figure>



9. &#x20;Generate new token 클릭 한 번더 클릭

<figure><img src="../.gitbook/assets/image (68).png" alt="" width="563"><figcaption></figcaption></figure>



10. Note 에 argo-toekn 을 입력하고 아래 scope 선택에 repo를 선택&#x20;

<figure><img src="../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>



11. 하단의 Generate token 클릭

<figure><img src="../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>



12. 출력되는 토큰값을 메모장에 저장

<figure><img src="../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

13. Cloud9 터미널에서 git repo와 연동하기위한 디렉토리 생성

```
mkdir git
cd git
```



14. 샘플 yaml 생성

```
cat <<EOF > sample-dp.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: sample-app
  namespace: default
  labels:
    app: sample-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: sample-app
  template:
    metadata:
      labels:
        app: sample-app
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
EOF
```

14. git repo 연동

```
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/<USERNAME>/myrepo.git
```



15. git username, password 등록

```
git config --global credential.helper store
git config --global user.name <GITHUB USERNAME>
git config --global user.email <GITHUB EMAIL ADDRESS>
git config --global user.password <GITHUB PAT>
```



15. git push (username : github 계정명 입력 / password : 메모장에 저장했던 token 값 입력)

```
git push -u origin main
```

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

16. github 페이지로 이동하여 푸시(업로드)되었는지 확인

<figure><img src="../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>
