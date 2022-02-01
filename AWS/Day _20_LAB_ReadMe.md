Lab: Deploy A Kubernetes Application

Tools used: Kubectl, Amazon EKS & Elastic Load Balancing

Created AWS IAM roles w/ AmazonEKSClusterPolicy policy
![1_Roles](https://user-images.githubusercontent.com/91057035/151870785-cb4530e9-f829-4831-8994-63326dadaed2.jpg)


Created EKS cluster & master node
![2_EKS_Clusters](https://user-images.githubusercontent.com/91057035/151870846-0fe03ed0-41fe-4808-a56a-1ce21dad1b60.jpg)


Created a Node Group with AmazonEKSworkerNodePolicy, AmazonEKS_CNI_Policy & AmazonEC2ContainerRegistryReadOnly Policy
![3_Nodes_Group](https://user-images.githubusercontent.com/91057035/151870848-5bffbc65-bee8-4c30-8aef-ffff8b54cd78.jpg)


Installed Kubectl

![4_Kubectl1](https://user-images.githubusercontent.com/91057035/151894142-da733aa7-9b5f-4227-86d3-73c2c2631c75.jpg)


Created & configured Kubeconfig to establish communication between local laptop and the EKS cluster
![5_AWS_CLI1](https://user-images.githubusercontent.com/91057035/151896231-adc3226a-600a-4888-a5d7-14ec6261a954.jpg)


![6_KubeConfig](https://user-images.githubusercontent.com/91057035/151896565-1c1a873b-9156-4a47-bf92-afc28f612b40.jpg)


Test Configuration

![7_Kubectl2](https://user-images.githubusercontent.com/91057035/151897168-1fc7e617-67b0-4a8a-9b40-4bf0b2cdf672.jpg)


![8_Kubectl3](https://user-images.githubusercontent.com/91057035/151897694-520e602c-b5b0-4c4c-beae-61a90eedd2c9.jpg)
![9_Kubectl4](https://user-images.githubusercontent.com/91057035/151897747-17936e5e-f423-46fa-8899-69b24ac29d36.jpg)


Deployed a sample Kuberbetes application onto cluster
![10_K8_app_deployment](https://user-images.githubusercontent.com/91057035/151897798-8497c067-5d72-4ef9-9552-b7c9457b6849.jpg)


Application & Pod status verification
![11_App_Pod_details](https://user-images.githubusercontent.com/91057035/151897837-62bce240-d782-4c95-ad23-7a2e0f412ab2.jpg)


Deleting resources 
![12_EKS_ClustersDelete](https://user-images.githubusercontent.com/91057035/151897856-943d664b-c5da-449c-ac9b-0976eb6ca0b1.jpg)
