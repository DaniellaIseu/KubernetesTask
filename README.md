# KubernetesTask

![Part 1 Image](images/part1_image.jpg)
*This is the output for Part 1 of the Kubernetes task.*



![Part 2 Image](images/part2_image.jpg)
*This shows the output for Part 2 of the Kubernetes task.*



![Nodes and services](images/working_nodes_n_svs.jpg)
*This demonstrates the working nodes and services in the Kubernetes cluster.*



## Part 3 
Objective:
Improve application resilience and performance by configuring cache persistence and transitioning to a replicated PostgreSQL database setup in Kubernetes.

What was done:
Enabled Persistent Caching for the Stock API:

Configured a Kubernetes emptyDir volume mounted at /cache to retain cache data across Pod restarts (non-persistent but survives restarts).

Replaced old single-instance database with a replicated PostgreSQL setup:

Updated API configurations:

products-api connects to the primary database instance.

stock-api connects to the secondary instance (read-only).

Applied and restarted the APIs to load the new config

## Part 4 
Objective:
Expose services using standard HTTP ports and clean DNS names using an Ingress controller.

What was done:
Deployed an Ingress Controller (used from previous labs).

Configured Ingress routes for:

Web app: http://widgetario.local

Products API: http://api.widgetario.local

Configuration updates:
Updated Kubernetes Ingress specs for web and products-api services.

Verified DNS routing and ensured the application remained fully functional under the new domain names.
## Part 5
Helm Chart Customization
Customized chart with UAT-specific values in uat.yaml.
'''bash 
webImage: widgetario/web:21.03-v2
papiImage: widgetario/products-api:21.03
sapiImage: widgetario/stock-api:21.03

## Part 6
Ingress Configuration
Added ingress.yaml template.
Used widgetario.uat as the domain.

## Part 7 
## Files and Structure

- `uat.yaml`: Helm values file customized for the UAT environment.
- Helm chart located in `helm/widgetario` .
- Kubernetes commands and deployment manifests used for Part 7.

## How to Deploy
 Ensure you have Kubernetes and Helm installed and configured.
![Screenshot 2025-05-16 174650](https://github.com/user-attachments/assets/cdb795d5-97bc-4590-864b-a42bc418285c)

##Troubleshooting Tips
If pods show ImagePullBackOff:
Ensure correct image name and tag in uat.yaml.
Ensure image is publicly available on Docker Hub.

kubectl get pods -n widg-uat
Forward port and access the app:
kubectl port-forward -n widg-uat deployment/widg-uat-widgetario 8080:80
