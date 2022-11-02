# Devtron - Kubernetes Dashboard for Helm

![](https://user-images.githubusercontent.com/72245772/199556647-eed3cd12-a944-4e09-af4f-0a2d03ce742f.png)


Helm is one of the most adopted package managers for deploying applications to Kubernetes. 
Though it reduces the complexities of deploying applications on Kubernetes, the Helm CLI comes with several challenges that we believe can be solved with a **Helm Dashboard**.

## 📕 Overview

The intuitive Helm Dashboard offers a UI-driven approach for managing the lifecycle of Helm Applications, abstracting out all the complexities and challenges.

Through the dashboard, one can:
- Install and manage custom helm charts
- See manifest diff of past revisions
- Easily rollback or upgrade between different versions
- Seamlessly integrate and deploy various charts using [Chart Groups](https://docs.devtron.ai/usage/deploy-chart/chart-group)

## 🖱 Installation

Before you begin, you must create a [Kubernetes cluster](https://kubernetes.io/docs/tutorials/kubernetes-basics/create-cluster/) (preferably K8s 1.16 or higher) and install [Helm](https://helm.sh/docs/intro/install/).

### Install Devtron with Helm Bundle

Run the following command to install the latest version of Devtron with Helm bundle:

```bash
helm repo add devtron https://helm.devtron.ai
```
```bash
helm install devtron devtron/devtron-operator --create-namespace --namespace devtroncd
```

### Access Devtron

**URL**: Use the following command to get the dashboard URL:

```bash
kubectl get svc -n devtroncd devtron-service -o jsonpath='{.status.loadBalancer.ingress}'
```

### Credentials

**UserName**:  `admin`
**Password**:   Run the following command to get the admin password: 
(For Devtron version **v0.6.0** and higher)

```bash
kubectl -n devtroncd get secret devtron-secret -o jsonpath='{.data.ADMIN_PASSWORD}' | base64 -d
```

### Installation status

The above install command starts the Devtron-operator, which takes a few minutes to spin up all of the Devtron microservices one by one. You may check the status of the installation with the following command:

```bash
kubectl -n devtroncd get installers installer-devtron \
-o jsonpath='{.status.sync.status}'
```

The command executes with one of the following output messages, indicating the status of the installation:

* **Downloaded**: The installer has downloaded all the manifests, and installation is in-progress.
* **Applied**: The installer has successfully applied all the manifests, and the installation is complete.

## 🖥 Simplified Access Management

The Helm Dashboard simplifies the complexity of cross-team collaboration by internally inheriting RBAC (Role Based Access Control) and at the same time, abstracting out its complexities through an intuitive UI.

The fine-grained [access management](https://docs.devtron.ai/getting-started/global-configurations/authorization/user-access) is spread out across various levels, such as: 
- View only
- Build and Deploy
- Admin
- Manager
- Super Admin

These can be easily configured for each user across various teams, within seconds!


## 📟 Active Resources Monitoring

With the dashboard, it becomes effortless to actively monitor all the Kubernetes resources deployed using Helm charts. 
Real-time information about the `health` and `status` of the deployed application can be viewed at once through the dashboard.

## 📦 Optimized Resource Grouping

Debugging an application through the Helm CLI can be very challenging as the number of deployed K8s resources increase.

Devtron creates a seamless debugging environment for you by providing optimized resource grouping within different `buckets`, making it easier to debug if any issue arises!

You even have the power to check real-time logs of any workload and exec into the terminal, just using the Dashboard UI 🚀

## ⚡️ Multi-cluster Application Management

The Dashboard works as a unified platform to easily manage your deployments across a multi-cluster environment, irrespective of the cloud providers.

## 💭 Support for Workload Hibernation

An out-of-the-box support to quickly scale up or down your workloads within a few clicks, enables to have more control over the resources being consumed and is effective for `non-prod` or `staging` environments. 

## 💪 Trusted By
 
The Helm Dashboard is being used and trusted by enterprises and communities all across the globe:

- [Delhivery](https://www.delhivery.com/)
- [BharatPe](https://bharatpe.com/)
- [Livspace](https://www.livspace.com/in)
- [Moglix](https://www.moglix.com/) 
- [Xoxoday](https://www.xoxoday.com/)
 
## 👥 Community & Support
 
Get updates and chat with project maintainers, contributors, and community members
- Follow [@DevtronL](https://twitter.com/DevtronL) on Twitter
- Raise feature requests, suggest enhancements, and report bugs in our [GitHub Issues](https://github.com/devtron-labs/helm-ui/issues)
- Interested to contribute? Be sure to check out [Devtron on GitHub](https://github.com/devtron-labs/devtron) 🌟
- Articles, How-tos, Tutorials - [Devtron Blogs](https://devtron.ai/blog/)
 
### Join us on Discord 

<p>
<a href="https://discord.gg/jsRG5qx2gp"><img src="https://invidget.switchblade.xyz/jsRG5qx2gp" alt="Join-Devtron"></a>
</p>

## :bookmark: License
 
Devtron Helm Dashboard is licensed under [Apache License, Version 2.0](LICENSE)