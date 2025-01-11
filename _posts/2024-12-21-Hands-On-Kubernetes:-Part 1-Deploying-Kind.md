When diving into Kubernetes, having a reliable local development environment is crucial. In this post, I'll walk through setting up a local Kubernetes cluster using KIND (Kubernetes IN Docker) and deploying a simple application to it.

#### Assumptions

- **Quick Read:** [link](https://matcham89.github.io/Hands-On-Kubernetes-Part-2-Deploying-Vault/)
- **Laptop / Machine to run KIND:** (Linux/Mac/Windows)
- **Docker Engine installed and logged in:** [guide](https://docs.docker.com/engine/install/)
- **kubectl installed:** [guide](https://kubernetes.io/docs/tasks/tools/)
- **IDE installed:** (vim/nvim/Visual Studio Code)
- **Go installed:** [guide](https://go.dev/doc/install)



#### KIND Installation

The installation steps are straightforward and documented well [here](#).



#### Setting Up Our Cluster

Let's start by creating a KIND cluster with one control plane node and two worker nodes running Kubernetes v1.32.0.

We can create this using a simple configuration file and the KIND CLI:

##### Create the cluster by running:
*(Command to create the cluster goes here)*



#### Test Application

We'll use a simple Flask web application that demonstrates environment variable configuration and secret management. Here's the current structure and the application:

##### Application Tree:
*(Application tree structure goes here)*

##### Dockerfile:
*(Dockerfile contents go here)*



#### Deploying to Kubernetes

With our application containerized, we can deploy it to our cluster.

##### Create the following files:
*(Details about the required manifest files go here)*



#### Setting Up Ingress Controller

KIND provides its own ingress controller, which we can deploy with. Detailed [here](#).

To handle external IPs locally, we'll need KIND's cloud provider. Detailed [here](#).

Running `cloud-provider-kind` will attach an external IP to our ingress controller. In my case, it looks like this:
*(Details of the external IP setup go here)*



#### Final Configuration

The last step is to update our `/etc/hosts` file to route traffic to our applications:  
*(Instructions for updating the `/etc/hosts` file go here)*  
*(Be sure to update the IP address with the output from your controller)*



#### What We've Accomplished

At this point, we have:

1. A functioning Kubernetes cluster with one control plane and two worker nodes.
2. Two deployed applications with their own services.
3. An ingress controller handling external traffic.
4. Local DNS resolution for our applications.

You can now access the applications by visiting:

- [http://app-a.local](http://app-a.local)
- [http://app-b.local](http://app-b.local)



#### Key Takeaways

- **KIND** provides a robust local Kubernetes environment.
- The built-in ingress controller simplifies local access to applications.
- Environment variables offer a flexible way to configure applications.
- Local DNS configuration enables seamless access to your services.



This setup provides a solid foundation for local Kubernetes development. In the next part, we'll explore further and introduce tools like **Vault** for secret management.