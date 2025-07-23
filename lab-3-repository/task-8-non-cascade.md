# Task 8 - Non cascade

1. Application 에서 Delete 클릭

<figure><img src="../.gitbook/assets/image (91).png" alt="" width="563"><figcaption></figcaption></figure>

2. sampleapp을 입력하고, Non cascade를 선택한 뒤 OK 클릭

<figure><img src="../.gitbook/assets/image (92).png" alt="" width="563"><figcaption></figcaption></figure>



3. 삭제 확인

<figure><img src="../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>



4. Cloud9 에서 리소스확인

```
kubectl get ns
```

<figure><img src="../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>



```
kubectl get all -n syncwave-namespace
```

<figure><img src="../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>
