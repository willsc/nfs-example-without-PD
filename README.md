# nfs-example-without-PD


Notes:

```

Nodepool management:

Change machine type in nodepool.


 gcloud config set container/cluster test-cluster
Updated property [container/cluster].

gcloud container node-pools list --zone europe-central2-a
NAME          MACHINE_TYPE  DISK_SIZE_GB  NODE_VERSION
default-pool  e2-medium     100           1.17.17-gke.1101


gcloud container node-pools create foo-pool --cluster test-cluster --zone europe-central2-a

WARNING: Starting with version 1.19, newly created node-pools will have COS_CONTAINERD as the default node image when no image type is specified.
Creating node pool foo-pool...done.
Created [https://container.googleapis.com/v1/projects/inspiring-cat-308916/zones/europe-central2-a/clusters/test-cluster/nodePools/foo-pool].
NAME      MACHINE_TYPE  DISK_SIZE_GB  NODE_VERSION
foo-pool  e2-medium     100           1.17.17-gke.1101

Turn on autoscaling on the node pool:
gcloud container clusters update test-cluster --enable-autoscaling --node-pool foo-pool --max-nodes=6 --min-nodes=3 --zone europe-central2-a



Delete node-pool:

gcloud container node-pools delete foo-pool --zone europe-central2-a
The following node pool will be deleted.
[foo-pool] in cluster [test-cluster] in [europe-central2-a]

Do you want to continue (Y/n)?


Create node-pool of specified machine type:
gcloud container node-pools create foo-pool --machine-type=n1-standard-4 --enable-autoscaling --max-nodes=6 --min-nodes=3  --cluster test-cluster --zone europe-central2-a




```


