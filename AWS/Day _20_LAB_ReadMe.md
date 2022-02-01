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


![7_AWS_CLI2](https://user-images.githubusercontent.com/91057035/151898313-a1578029-54f3-4ab9-96fb-a5cd76e54f2f.jpg)


Test Configuration

![7_Kubectl2](https://user-images.githubusercontent.com/91057035/151897168-1fc7e617-67b0-4a8a-9b40-4bf0b2cdf672.jpg)


![8_Kubectl2](https://user-images.githubusercontent.com/91057035/151898677-863d5962-f1a4-4853-be5d-5c322680d61b.jpg)
![9_Kubectl3](https://user-images.githubusercontent.com/91057035/151898664-0ef14a48-9f0d-446e-80bb-916df3d9e47c.jpg)
![10_Kubectl4](https://user-images.githubusercontent.com/91057035/151898639-174d6f8c-510a-40f8-ac00-b824d3435d11.jpg)


Deployed a sample Kuberbetes application onto cluster
![11_K8_app_deployment](https://user-images.githubusercontent.com/91057035/151898622-90edbd0d-8fbe-494d-bde2-7b691d980ada.jpg)


Application & Pod status verification
![12_App_Pod_details](https://user-images.githubusercontent.com/91057035/151898594-9bee1eae-1939-4ebf-887a-9dca4472ec79.jpg)

Deleting resources 
![13_EKS_ClustersDelete](https://user-images.githubusercontent.com/91057035/151898572-49592bf9-e63d-4965-bae6-6912aa52b350.jpg)
