# Updates and rollbacks

Question:
- Create a redis deployment of 2 pods with an update strategy 'recreate' 
- Create an nginx deployment of 2 pods with an update strategy 'rollingUpdate'
- Pass in entrypoint and argument to a pod
- Pass in an environment variable to a pod
- Pass in an environment variable to a pod, using configmap
- Pass in an environment variable to a pod, using secret
- Create secret with 3 values, mount in pod


- Create configmap and use it in a pod
<details><summary>Solution</summary>
<p>

```bash
kubectl create configmap my-configmap --from-literal=key1=config1 --dry-run=client -o yaml
```
or
```bash
kubectl create configmap my-configmap --from-file=app_config.txt
```

Use it in a pod definition

mysql.yml
```yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: mysql
  name: mysql
spec:
  containers:
  - image: mysql
    name: mysql
  envfrom:
    - configMapRef:
        name: my-configmap

```

</p>
</details>
