[Version Information](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html)

[[EKS]] has version much like the main [[Kubernetes]]. There will be a delay between the releases to allow [[AWS]] to integrate the new features.

## If using [[EKS Compute EC2]] and not workload groups

Assuming using green and blue [[ASG]]s. A ASG refers to the current live [[ASG]], B ASG to the other.

1. Check for any deprecated API versions
	1. These can be found [here](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)
	2. Can also use the [[Kubent]] tool
2. Check for new versions of any [[EKS add-ons]]
3. Get the new [[EKS]] version [[AMI]]
4. Make sure the B is scaled down
	1. Check for in scale protection
5. Update the launch template for B with the new [[AMI]]
6. Update the [[EKS]] version
	1. Either through the console
	2. Or, with the command line
7. Scale up B to at least the same as A
8. Check B is happy and taking traffic
9. Cordon and drain the pods in A
10. Scale down A
11. Update the launch template for A with the new [[AMI]]


## If using [[EKS Compute Fargate]]