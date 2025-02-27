# Installing the Kubernetes Metrics Server<a name="metrics-server"></a>

The Kubernetes Metrics Server is an aggregator of resource usage data in your cluster, and it is not deployed by default in Amazon EKS clusters\. For more information, see [Kubernetes Metrics Server](https://github.com/kubernetes-sigs/metrics-server) on GitHub\. The Metrics Server is commonly used by other Kubernetes add ons, such as the [Horizontal Pod Autoscaler](horizontal-pod-autoscaler.md) or the [Kubernetes Dashboard](dashboard-tutorial.md)\. For more information, see [Resource metrics pipeline](https://kubernetes.io/docs/tasks/debug/debug-cluster/resource-metrics-pipeline/) in the Kubernetes documentation\. This topic explains how to deploy the Kubernetes Metrics Server on your Amazon EKS cluster\.

**Important**  
Don't use Metrics Server when you need an accurate source of resource usage metrics or as a monitoring solution\.

**Deploy the Metrics Server**

1. Deploy the Metrics Server with the following command:

   ```
   kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
   ```

1. Verify that the `metrics-server` deployment is running the desired number of pods with the following command\.

   ```
   kubectl get deployment metrics-server -n kube-system
   ```

   Example output:

   ```
   NAME             READY   UP-TO-DATE   AVAILABLE   AGE
   metrics-server   1/1     1            1           6m
   ```