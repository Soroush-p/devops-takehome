# 


Deployment and RollingUpdate:

Using the deployment instead of replicaSet gives the ability to autoscale based on the CPU and other metrics. Each app have a seperate deployment to able to scale indepentently, one for Shifts and one for Users. Strategy stanza added as RollingUpdate to allow the rolling update and rollback.


Autoscaling:

Resources Stanza under the pod spec in the deplyment added so Kubelet can read the CPU utilization for each pod. Asumming Metric Server deployed, creating Horzontal Autoscaling (HPA) object for each deployment to allows autoscaling when the average CPU load on all desired pods reached 70%.


RBAC:

Using role based access control to authorize DEV team. Creating role and rolebinding for DEV team to access the resources only in DEV namespace.


Managing multiple clusters:




Autoscaling based on Network latency:

Nginx ingress controller provide some metrics including number of active connections, once number of active connetcions increase that causes the ingress controller pod can't handle the number of connection and need more resources to able to address more connections. Premethus can be used to collect the metrics from Nginx and KEDA bridges those metric and feed them to Horitontal Pod Autoscaler.



