# Clustermaintenance

Question:
- Back up all definitions
<details><summary>Solution</summary>
<p>
```bash
kubectl get all -A -o yaml > all.yaml
```
</p>
</details>

Question:
- Back up the ETCD server
<details><summary>Solution</summary>
<p>
```bash
ETCDCTL_API=3 etcdtl snapshot save snapshot.db
```
</p>
</details>

Question:
- Restore from an ETCD snapshot
<details><summary>Solution</summary>
<p>
```bash
ETCDCTL_API=3 etcdtl snapshot restore snapshot.db --data-dir /var/lib/etcd-from-backup
```

Don't forget to specify:
```bash
--endpoints=
--cacert=
--cert=
```


Then configure ETCD to use the new data directory

</p>
</details>