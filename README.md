# KubernetesTask

![Part 1 Image](images/part1_image.jpg)
*This is the output for Part 1 of the Kubernetes task.*



![Part 2 Image](images/part2_image.jpg)
*This shows the output for Part 2 of the Kubernetes task.*



![Nodes and services](images/working_nodes_n_svs.jpg)
*This demonstrates the working nodes and services in the Kubernetes cluster.*


#Part 7 
## Files and Structure

- `uat.yaml`: Helm values file customized for the UAT environment.
- Helm chart located in `helm/widgetario` .
- Kubernetes commands and deployment manifests used for Part 7.

## How to Deploy Part 7

1. Ensure you have Kubernetes and Helm installed and configured.
![Screenshot 2025-05-16 174650](https://github.com/user-attachments/assets/cdb795d5-97bc-4590-864b-a42bc418285c)


3. Deploy the Helm chart:

```bash
helm install widg-uat ./helm/widgetario -f hackathon/files/helm/uat.yaml -n widg-uat --create-namespace
