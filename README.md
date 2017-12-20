# kube-fed-rancher

WIP to setup federation on Kubernetes (Rancher 1.6)

1. Clone the k8s federation repo to build `kubefed` https://github.com/kubernetes/federation

```
git clone https://github.com/kubernetes/federation.git
cd federation
make
cp _output/bin/kubefed /usr/local/bin/kubefed
chmod a+x /usr/local/bin/kubefed
```

2. Deploy Rancher 1.6 with Kuberentes 1.8 or higher. I use https://github.com/wjimenez5271/tf-do-rancher

3. Deploy NFS client provisioner and NFS storage class resources

```
kubectl create -f nfs-client-provisioner.yaml
kubectl create -f storage-class.yaml
```

4. Run `kubefed` init

```
kubefed init gc --host-cluster-context=DigitalOcean --dns-provider="coredns"  --dns-zone-name="global."
```
