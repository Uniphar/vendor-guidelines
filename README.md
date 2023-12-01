# 3rd Party Vendor guidelines

At technology in Uniphar, our preference is to work with vendors that embrace the same principles and values that we have, so that projects produce outcomes and deliverables that are good fits for the various internal technical teams working at Uniphar.

In parallel with the above, we also empower external vendor teams and we allow for a degree of choice so that some decisions match the external vendor team way of working. So things like branching strategy, actions to run during CI/CD, etc. we give external teams the power of choice.

We have a detailed set of [DevOps guidelines](https://github.com/Uniphar/devops-guidelines) already on github.

We also have a set of questions aimed at [vendor accessment here](./vendor-qa.md).

## Kubernetes

Our prefered deployment target is Kubernetes, we run and operate multi-region clusters, so applications and deployments should be designed for multi-region and avoid any persistency mechanisms that are region specific.

Because of the above we prefer to work with vendors that are experiences with deployment, running and operating applications running on Kubernetes clusters, that can easily adapat to how we inject secrets into applications and how own ingress stack:

- Azure Frontdoor or API Manager
- Azure App Gateway (app-gateway ingress) or Azure Load Balancer (nginx ingress)
- Pod

## Automate everything

We live and die by the principle that any application, deployment or piece of infrastructure should be driven by code, because our entire review process relies on pull requests and CI/CD pipelines. Our current stack for this is:

- PowerShell
- Bicep
- DSC for Windows
- Ansible for Linux
- Helm charts

But we are open to other stacks, as long as their working files are friendly to pull requests. We are also open to automation driven by specific platform CLIs as long as the heavy configuration is done in friendly pull request formats like YAML or JSON.

## Lean and Open Source code

We are believers that less code is most the times code that can change faster. So we do not engineer anything that doesn't need to be engineered and we don't practice futorology when designing code: _What if in the future we need to [Insert Preduction Here]?_

Open Source is always the option when contrasted with engineering customizable solutions, so we avoid working with teams and vendors that like to engineer their own solutions to problems the open source comunity has already solved, instead of contributing to those open source projects.

Working with vendors that themselves are authors or contributors to open source projects that are widely used is a preference for Uniphar.

## Application lifecycle in Uniphar

We are using an [Azure DevOps tenancy](https://dev.azure.com/UnipharGroup/) for backlog and boards and github organization for code and CI/CD pipelines through github actions. We want new projects to use the same ALM framework as we use for everything else, so we bring vendor teams into Azure DevOps and github and they build the project artefacts there.

For Azure DevOps we usually onboard original identities (you@vendor.com) and for github we just bring your github ID in, we don't use the SAML authentication forcing the @uniphar.ie tenancy to be used.

The deployment service principles will be setup by the Uniphar DevOps team for the application repos to be able to host CI/CD that are empowered to do deployments against the target project infrastructure.
