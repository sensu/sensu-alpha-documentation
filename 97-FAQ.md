# Frequently Asked Questions

**Q: Does Sensu have any storage limitations?**

We'd love it if you could write checks as big as your heart desires. However, Etcd has some performance constraints around `mean time to recovery` (see [etcd-dev discussion](https://groups.google.com/forum/#!topic/etcd-dev/vCeSLBKC_M8 "etcd-dev discussion") for more details). In order to optimize MTTR and your experience with Sensu, we've determined the max http request size to be 512K bytes.
