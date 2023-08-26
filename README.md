# cronjob-net-6
 Creation of a CRON job (background task) with C# and .NET 6 in Kubernetes
 http://localhost:8080/apis/batch/v1/namespaces/default/cronjobs

kubectl get nodes
NAME             STATUS   ROLES           AGE     VERSION
docker-desktop   Ready    control-plane   4m24s   v1.27.2

kubectl get nodes
NAME             STATUS   ROLES           AGE     VERSION
docker-desktop   Ready    control-plane   5m44s   v1.27.2

kubectl get cronjobs
NAME        SCHEDULE      SUSPEND   ACTIVE   LAST SCHEDULE   AGE
mycronjob   */5 * * * *   False     0        <none>          3m9s

kubectl get cronjob mycronjob
NAME        SCHEDULE      SUSPEND   ACTIVE   LAST SCHEDULE   AGE
mycronjob   */5 * * * *   False     0        <none>          3m30s

k

kubectl get pods
NAME                       READY   STATUS    RESTARTS   AGE
mycronjob-28217865-qf658   1/1     Running   0          70s

kubectl logs mycronjob-28217865-qf658
info: CronWorkerService.Worker[0]
      Worker running at: 08/26/2023 17:45:08 +00:00
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Production
info: Microsoft.Hosting.Lifetime[0]
      Content root path: /app


kubectl proxy --port=8080 &
Starting to serve on 127.0.0.1:8080
^C

 http://localhost:8080/apis/batch/v1/namespaces/default/cronjobs



 Reference Links:
 https://benbrougher.tech/posts/kubernetes-cron-job/#with-visual-studio
 https://crontab.guru/
 https://docs.docker.com/desktop/kubernetes/
 https://kubernetes.io/docs/tasks/job/automated-tasks-with-cron-jobs/
 https://kubernetes.io/docs/tasks/administer-cluster/access-cluster-api/
 https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/cron-job-v1/
 https://github.com/kubernetes-client/csharp/blob/master/examples/simple/PodList.cs