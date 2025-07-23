# Task 7 - Self Healing

1. kubectl 명령으로 Pod 스케일링&#x20;

```
kubectl scale deploy -n syncwave-namespace syncwave-app --replicas=10
```



2. 동작확인

```
kubectl get pod -n syncwave-namespace
```

<figure><img src="../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>



3. ArgoCD 에서도 확인

<figure><img src="../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>

4. 다시 replicas 원상복구

```
kubectl scale deploy -n syncwave-namespace syncwave-app --replicas=1
```

<figure><img src="../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>



5. ArgoCD Application 에서 DETAIL을 클릭하고, SELFHEAL 을 클릭, OK를  클릭하여 기능 활성화

<figure><img src="../.gitbook/assets/image (88).png" alt="" width="521"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (90).png" alt="" width="312"><figcaption></figcaption></figure>

6. 1번 명령을 다시 수행하고, 즉시 ArgoCD UI에서 동작확인

```
kubectl scale deploy -n syncwave-namespace syncwave-app --replicas=10
```



Pod 가 생성이 되다가 다시 삭제되어 1개로 돌아가는 동작 확인.

