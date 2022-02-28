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

![8_Kubectl2](https://user-images.githubusercontent.com/91057035/151899083-1efa0772-9267-4c7c-a49c-9769d4ff74ab.jpg)


Deployed a sample Kuberbetes application onto cluster
![9_K8_app_deployment](https://user-images.githubusercontent.com/91057035/151899181-c2d03cdc-f436-48e1-84b2-a746d1d46973.jpg)


Application & Pod status verification
![10_App_Pod_details](https://user-images.githubusercontent.com/91057035/151899211-464571a8-3fb7-4339-86c1-9c423d60e103.jpg)


Deleting resources 
![13_EKS_ClustersDelete](https://user-images.githubusercontent.com/91057035/151898572-49592bf9-e63d-4965-bae6-6912aa52b350.jpg)
