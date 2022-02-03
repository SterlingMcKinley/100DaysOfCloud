Created an EKS cluster

![created_eks_cluster](https://user-images.githubusercontent.com/91057035/152416237-a7dff8cf-3bd5-4ff4-b8ca-8f76e3a5af5a.png)


![created_iam_roles_eks_cluster](https://user-images.githubusercontent.com/91057035/152416392-8c9dd245-adea-4ba7-b24e-4616dc8e874b.png)


Create worker node(s)

![create_worker_nodes](https://user-images.githubusercontent.com/91057035/152416643-fd0f1c56-a9b1-47b4-8b1e-00303b2032ec.png)

![created_worker_nodes2](https://user-images.githubusercontent.com/91057035/152416680-5fff3462-4491-4f9d-8bc2-a6ec178a7bef.png)

![created_worker_nodes3](https://user-images.githubusercontent.com/91057035/152416696-46dfa1d5-55a0-4e01-b936-2ed92c315bb4.png)


Deploy KMS via kubectl

![deploy_kms](https://user-images.githubusercontent.com/91057035/152416813-695c6332-074b-44e4-b952-ecac1068ce37.png)


Adding the Kubernetes Dashboard manifest to the cluster (eks-cluster)

![k8_dashboard_config](https://user-images.githubusercontent.com/91057035/152416987-4746ac2d-e639-4a5b-9878-05930fca37cd.png)


Created a yaml file ( eks-admin-service-account.yaml) This file defines a service account and cluster role binding called “eks-admin”

![k8_dashboard_config](https://user-images.githubusercontent.com/91057035/152417194-ceaeb46d-4144-4bc6-8753-8044b42aab5e.png)


Retrieve authentication token for the eks-admin service account. The authentication will grant access to the dashboard.

Commands:

-kubectl get secrets

-kubectl describe secret {token-name}
  
![get_auth_token](https://user-images.githubusercontent.com/91057035/152417367-b9795a80-1787-4f28-8bd2-465ac2805fad.png)
  
  
  
Start kubectl proxy

![start_proxy](https://user-images.githubusercontent.com/91057035/152417462-94b3fc2a-c28c-4377-8d1b-c8a3d656d4d5.png)

  
Kubernetes Dashboard
•	Go to a browser and enter the link below:
  
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#!/login
  
•	With the “Token” option selected, copy the authentication token from the command-line and pasted it onto the “Enter Token*”  (Token will be encrypted)
  
  ![K8_dashboard_UI](https://user-images.githubusercontent.com/91057035/152417969-dd30d322-e439-4817-bdb7-ddc97fc07d61.png)

  
Kuberbetes Dashboard UI
  
![K8_dashboard_homepage](https://user-images.githubusercontent.com/91057035/152418354-cb1a0e72-2623-436e-b411-374c31af2283.png)


  
