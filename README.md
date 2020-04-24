# Devops Test

Our test has three different topics which are:

1. Architecture & process definition (~1h30)
2. Kubernetes use cases (~2h)
3. Technical questions (~30min)

The whole test should roughly take 4 hours to complete.

# 1. Architecture & Process

For this section, we only expect documentation. You don’t need to code or deploy anything.

Let’s say we’re building a new infrastructure and platform from scratch. The platform we’re trying to build and deploy consists of a few applications and databases. It has to run on a Kubernetes stack.     

We’re expecting you to provide guidelines on what should be deployed with regards to the following requirements:

- We should have observability 
- Access to Kubernetes components must be secured. Some users have full access whereas some others may have limited access. 
- Our Kubernetes cluster should be fault tolerant, in the sense that a network outage in one cloud zone / region should not impact much our applications’ up-time
- Our Kubernetes cluster nodes should not have a public IP address. All incoming traffic should by handled by a Load-balancer
- Some of our applications should be deployed in a separate subnet
- Developers’ desktop environment should stick as close as possible to production 
- We must have a CI/CD
- We need an efficient backup strategy for data related services

Besides the building block of the infrastructure, we’d like to have information on how you would handle the following topics:


- How would you handle application configuration ?
- What processes and tools do you plan to use in order to have a proper "Infrastructure As Code" approach
- Would you recommend a full cloud approach ? Hybrid deployment ?
- Even though we’re not Netflix, what’s your opinion on chaos engineering ? Would you recommend it and, if so, what should be tested and how ?
- How would you deploy stateful applications such as databases ? Would you have them within Kubernetes and if so how would you manage them ?

Please provide information for each of the above poins. Once again, please just state how you would achieve these things.

# 2. Kubernetes

You will have to deploy a small Node.js app on Kubenetes from scratch.

The application soure code and instuctions to build and run it are available in the README file at https://github.com/oui-team/devops-interview/app.

What you need to produce:

- A dockerfile to build the application
- A manifest to deploy the app (you may pick your own: Kubernetes, Helm, …)
- A description of the components you would use to monitor the application (see the bonus part to include it in your manifest)
- A precise documentation of every component you will use
- A description of the complete CI/CD tooling you will use to deploy
- A successful and working deployment on Kubernetes
- An ingress and service that route incoming traffic to our application

We provide an external static IP address. We will send you the IP address and a domain name resolving to this IP.

We will pay extra attention to:

- Your Dockerfile
- How you handle configuration
- Your choices regarding deployment tools and monitoring
- Your manifests formats (helm, terraform, raw, ..)
- The scaling capabilities of your deployment

A Kubernetes cluster is available to deploy your app. You may use the public Docker Hub to publish your image.

## Bonus

Once deployed, we should be able to monitor the application: basic memory/CPU usage, HTTP codes, eventual errors…
So if you still have time:

- The deployed ingress should only allow whitelisted IP addresses
- Add a monitoring service in your manifest (like Grafana) and connect it
- Secure your app with a certificate (you can use LetsEncrypt)


# 3. Technical Questions (bonus)


1. Imagine that one of your colleagues accidentally applied all the “production” config-maps to the “beta” environment.
    -  What impacts could this have ?
    - How would you
        - Get things running properly again ?
        - Find what has been impacted ?
        - Prevent a re-occurrence of the issue ?
2. There is a large amount of non-public data stored in a MySQL database located on a virtual machine that needs to be accessed by typical well-maintained and tested APIs as well as by data engineers in “exploratory” mode (they don’t know which data they need until they need it). This VM is mounted on a RAID 4 disk system and the disk space is running low.
Describe, with diagrams if needed, the systems and checks you would implement to ensure the data can be accessed by all parties in a secure manner. What would you do about the disk space ? 

Be sure to detail the pros and cons of your answers 




