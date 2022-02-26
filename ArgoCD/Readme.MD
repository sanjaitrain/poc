https://argo-cd.readthedocs.io/en/stable/getting_started/

Ensure argocd is installed and then forward port.

kubectl port-forward svc/argocd-server -n argocd 8080:443

admin password
---------------

sass273491@ROL00120:~/jenkins/jenkins$ kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
-TaQsPju7iaXfJf-

Now you should be able to access argocd under https://127.0.0.1:8080/

sass273491@ROL00120:~/poc/poc/ArgoCD$ k get all -n argocd
NAME                                     READY   STATUS    RESTARTS   AGE
pod/argocd-application-controller-0      1/1     Running   0          36h
pod/argocd-dex-server-59d44b9f99-tmlb6   1/1     Running   0          36h
pod/argocd-redis-79bdbdf78f-jr6xm        1/1     Running   0          36h
pod/argocd-repo-server-b6f8cdc6f-5l5qt   1/1     Running   0          36h
pod/argocd-server-bdc697879-fqll4        1/1     Running   0          36h

NAME                            TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
service/argocd-dex-server       ClusterIP   10.99.91.218     <none>        5556/TCP,5557/TCP,5558/TCP   36h
service/argocd-metrics          ClusterIP   10.97.165.191    <none>        8082/TCP                     36h
service/argocd-redis            ClusterIP   10.102.148.31    <none>        6379/TCP                     36h
service/argocd-repo-server      ClusterIP   10.110.104.127   <none>        8081/TCP,8084/TCP            36h
service/argocd-server           ClusterIP   10.102.214.218   <none>        80/TCP,443/TCP               36h
service/argocd-server-metrics   ClusterIP   10.108.20.248    <none>        8083/TCP                     36h

NAME                                 READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/argocd-dex-server    1/1     1            1           36h
deployment.apps/argocd-redis         1/1     1            1           36h
deployment.apps/argocd-repo-server   1/1     1            1           36h
deployment.apps/argocd-server        1/1     1            1           36h

NAME                                           DESIRED   CURRENT   READY   AGE
replicaset.apps/argocd-dex-server-59d44b9f99   1         1         1       36h
replicaset.apps/argocd-redis-79bdbdf78f        1         1         1       36h
replicaset.apps/argocd-repo-server-b6f8cdc6f   1         1         1       36h
replicaset.apps/argocd-server-bdc697879        1         1         1       36h

NAME                                             READY   AGE
statefulset.apps/argocd-application-controller   1/1     36h


bf7f06bfb6bc4cb88c38f93aa03f4202