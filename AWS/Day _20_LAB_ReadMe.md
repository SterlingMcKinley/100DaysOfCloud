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


![8_KubeConfig](https://user-images.githubusercontent.com/91057035/151896998-86078754-2725-41cf-86bf-2a1eb4173fe5.jpg)


![9_Kubectl3](https://user-images.githubusercontent.com/91057035/151870860-75c9c6c1-2371-4a78-9c58-158a548e6170.jpg)
![10_Kubectl4](https://user-images.githubusercontent.com/91057035/151870861-fc074764-74c4-4037-9d6f-ce01f7b5a760.jpg)


Deployed a sample Kuberbetes application onto cluster
![11_K8_app_deployment](https://user-images.githubusercontent.com/91057035/151870863-ac7a0a06-2730-4081-a727-f641e0425852.jpg)


Application & Pod status verification
![12_App_Pod_details](https://user-images.githubusercontent.com/91057035/151870864-302b7d2e-e4e3-4137-aa32-37d23c5175f9.jpg)


Deleting resources 
![13_EKS_ClustersDelete](https://user-images.githubusercontent.com/91057035/151880921-44a003a8-2622-420c-91bd-1c2bc5bfd93f.jpg)
