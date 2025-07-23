# Task 5 - Prune

1. 이전 실습에 사용하던 Application 의 Detail 클릭

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>





2. PRUNE 활성화 여부 확인 (비활성화)

<figure><img src="../.gitbook/assets/image (63).png" alt="" width="563"><figcaption></figcaption></figure>



3. git 디렉토리에서 sample-svc.yaml 삭제

```
ls
rm sample-svc.yaml
```

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>



4. git push

```
git add .
git commit -m "delete svc"
git push -u origin main
```



5. Refresh 클릭

<figure><img src="../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>





6. Sync 상태가 변경된 것 확인, Application 에서 svc는 삭제 되지 않은 것 확인

<figure><img src="../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>



7. github 저장소 확인, kubectl 명령으로 삭제여부 확인

```
kubectl get svc
```

<figure><img src="../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>





8. 다시 sample-svc.yaml 파일을 생성

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





9. 다시 git push 한 뒤 Refresh 를 클릭하여 sync 상태 확인

```
git add .
git commit -m "add svc"
git push -u origin main
```



<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>



10. 다시 DETAILS 를 클릭하고, PRUNE 의 ENABLE을 클릭, OK 클하여 활성화

<figure><img src="../.gitbook/assets/image (77).png" alt="" width="519"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (78).png" alt="" width="314"><figcaption></figcaption></figure>



11. 위 3\~5 과정을 반복 수행



12. 결과 확인

<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>
