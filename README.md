<a id="readme-top"></a>

<br />

<h3 align="center">Automated Kubernetes GitOps Platform</h3>

  <p align="center">
    A self-healing DevOps platform running locally on Kubernetes (k3d). This project demonstrates a GitOps workflow where infrastructure state is managed through code, featuring automated CI/CD pipelines, public ingress tunneling, and real-time observability.
    <br />
    <br />
  </p>
</div>



<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
  </ol>
</details>



## About The Project

This project simulates a production-grade Kubernetes environment locally. It transitions from manual infrastructure management to a fully automated GitOps methodology.

#### Key Highlights
* Automated GitOps Loop: Pushing to the `main` branch triggers a CI build, updates the deployment manifest with the new image SHA, and automatically syncs the cluster state via ArgoCD.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



### Built With

* Kubernetes: Lightweight container orchestration.
* Docker: Containerization of the Nginx web application.
* GitHub Actions: Continuous Integration (CI).
* ArgoCD: Continuous Delivery (CD).
* Traefik & Ngrok: Ingress control and secure public tunneling.
* Prometheus & Grafana: Observability and metric visualization.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



## Getting Started

### Prerequisites

* Docker Desktop
* `kubectl` & `k3d` CLI tools installed
* A Docker Hub account (for image registry)
* An Ngrok account (for the auth token)

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/PRAISE-THE-SUUUN/k8s-devops-project.git
   ```
2. Create the Kubernetes Cluster
   ```sh
   k3d cluster create mycluster --api-port 6443 -p "80:80@loadbalancer"
   ```
3. Install ArgoCD
   ```sh
   kubectl create namespace argocd
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   ```
4. Configure Ngrok Secret
   ```sh
   kubectl create secret generic ngrok-secret --from-literal=NGROK_AUTHTOKEN=your_token_here
   ```
5. Deploy the GitOps Application
* Access the ArgoCD UI.
* Connect this GitHub repository to ArgoCD and set the path to the `k8s/` directory.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



## Usage

#### How to test the automation:
1. Modify the `app/index.html` file.
2. Commit and push the changes to GitHub.
3. Watch the GitHub Actions tab successfully build and push the new image to Docker Hub.
4. Watch ArgoCD automatically detect the new image SHA tag in the `k8s/deployment.yaml` and sync the cluster.
5. Refresh your public Ngrok URL to see the changes.

<p align="right">(<a href="#readme-top">back to top</a>)</p>


[contributors-shield]: https://img.shields.io/github/contributors/github_username/repo_name.svg?style=for-the-badge
[contributors-url]: https://github.com/github_username/repo_name/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[stars-shield]: https://img.shields.io/github/stars/github_username/repo_name.svg?style=for-the-badge
[stars-url]: https://github.com/github_username/repo_name/stargazers
[issues-shield]: https://img.shields.io/github/issues/github_username/repo_name.svg?style=for-the-badge
[issues-url]: https://github.com/github_username/repo_name/issues
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[product-screenshot]: images/screenshot.png
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vue.js]: https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D
[Vue-url]: https://vuejs.org/
[Angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[Angular-url]: https://angular.io/
[Svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[Svelte-url]: https://svelte.dev/
[Laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[Laravel-url]: https://laravel.com
[Bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[Bootstrap-url]: https://getbootstrap.com
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com 
