# Deploy a React Application with a back-end API to Azure Static Web Apps

[Azure Static Web Apps][link_swaoverview] allows you to easily build
[React][link_reactjs] apps in minutes. This repo showcases a very basic React
application based on the [React
Quickstart Guide][link_reactqs] and how to deploy it to Azure Static Web Apps.  
The [API tutorial][link_apitut] extends this example with the simple back-end
API part using Azure Functions.

This repo is a template repo. You can [create your own copy of this
repo][link_repo] and start provisioning and deploying to a subscription of
yours.

[link_swaoverview]: https://docs.microsoft.com/azure/static-web-apps/overview
[link_reactjs]: https://reactjs.org/
[link_reactqs]: https://docs.microsoft.com/azure/static-web-apps/getting-started?tabs=react
[link_apitut]: https://learn.microsoft.com/en-us/azure/static-web-apps/add-api?tabs=react
[link_repo]: https://github.com/new?template_name=cloud-azure-staticwebdev-react-and-api&template_owner=id-unibe-ch

## Prerequisites

* A copy of this repo on GitHub, where you have full access rights
* An Azure subscription with permission to create resources
* The tools `git` and `az` (Azure LI CLI) installed on your local machine

## Setup

Clone your copy to your local machine and adjust the variables in the
provisioning script. Choose a meaningful workload name for your use case, adjust
the environment and set tags according your [tagging
strategy](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-tagging).

Now run the provisioning script. You have
to be logged in to the Azure CLI and have selected the right subscription.
Follow the onscreen instructions.

```bash
az login
./infra/provision.sh
```

The provisioning script creates a resource group and a static web app resource.
During these tasks, you are requested to authenticate with GitHub. This allows
the Azure CLI to commit the GitHub Actions workflow file to your repo. This
workflow will later deploy your React application site to the static web app.

## Local Web Development with SWA CLI

Local development and testing can be done using the SWA CLI (Node 18, 20 or 22
is needed):

```bash
npm install -D @azure/static-web-apps-cli
npx swa start build --api-location api
```

This starts two services, one for the API on port 7071 and one for the static
frontend on port 4280. Point your browser to http://localhost:4280.
