# Spark on Kubernetes

* Running Spark in the Cloud with dynamic and fast moving cloud infrastructure
* Kubernetes is the enterprise standard orchestration framework designed primarily for the cloud
* Running Spark in containers
* Started as a Kubernetes issue [Support Spark natively in Kubernetes](https://github.com/kubernetes/kubernetes/issues/34377) and moved to Apache Spark's [SPARK-18278 SPIP: Support native submission of spark jobs to a kubernetes cluster](https://issues.apache.org/jira/browse/SPARK-18278)
* one generic K8S RM for all applications (aware of the overall cluster state and infrastructure) while Spark is addressing resource needs by accessing the K8S API, through a plugin developed by the Spark on K8S project.

## Articles

1. [Introduction to Spark on Kubernetes](https://banzaicloud.github.io/blog/spark-k8s/)
