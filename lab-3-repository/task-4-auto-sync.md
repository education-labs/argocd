# Task 4 - Auto Sync

1. Application 메뉴에서 sampleapp Application 클릭

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>



2. DETAIL 클릭

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>



3. 하단 ENABLE AUTO-SYNC 클릭, OK 클릭

<figure><img src="../.gitbook/assets/image (57).png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (59).png" alt="" width="563"><figcaption></figcaption></figure>



4. sample-dp.yaml 의 replicas 를 2로 수정 한뒤 git push

```
vi sample-dp.yaml
```

<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>



```
git add .
git commit -m "replicas 2"
git push -u origin main
```



5. Application 의 Refresh 버튼을 클릭하여 수동 Refresh 를 진행하자마자 sync 작업이 진행되는 것을 확인

<figure><img src="../.gitbook/assets/image (61).png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

