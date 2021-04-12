# Azure Infrastructure Automation with Jenkins and Terraform Cloud

##Jenkins setup from Docker
<span style="color:black;">Contents</span>
- [Jenkins setup from Docker](#Jenkins-setup-from-Docker)
- [Terraform Cloud setup](#Terraform-Cloud-setup)
- [Terraform Scripts](#Terraform-Scripts)
- [Jenkins Pipeline](#Jenkins-Pipeline)
- [Azure Validation](#Azure-Validation)

## _**Jenkins setup from Docker**_
1. Install the Docker Engine from the following URL **[DockerEngine](https://docs.docker.com/engine/install/)** as per the environment.
2. If you are windows user skip step 1 and install the Docker Desktop from the following URL **[DockerDesktop](https://docs.docker.com/docker-for-windows/install/)**
3. Login to the Docker Hub with credentials if you don't have account create a new one from the following URL **[DockerHUB](https://www.docker.com/)**
4. Open the command promt and login to the Docker Hub with the below command by using the credentials

            * docker login
            
5. Once login successfull, seach for the jenkins images by using the below command

            * docker search jenkins
            
6. From the list download the jenkins/jenkins image by using the below command

            * docker pull jenkins/jenkins
            
7. Run the Jenkins container by using the below command

            * docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins
            
   Note1: Here two port mappings happened one is 8080 and 50000 if the port is already used then choose the another port
   Note2: Copy the Jenkins Password from the command prompt to unlock the Jenkins
8. Once the container is up and running state. Open the browser and hit the below URL

             **http://localhost:8080**
             
9. Install the required plugins while setting up Jenkins and finish the basic setup.
10.Go to the Jenkins Dashboard -> Manage Jenkins -> Manage Plugins, under the Available plugins tab search for the "Blue Ocean" and "Active Choices" plugins and install it with out restart.
11.For test the Blue Ocean UI hit the below URL

             **http://localhost:8080/blue**

![Jenkins Docker](https://github.com/lokpavan03/jenkinstf/blob/master/jpgs/Jenkins_docker.gif)

## _**Terraform Cloud setup**_
1. Create a Terraform Cloud account use the following URL **[TerraformCloud](https://www.terraform.io/cloud)** if account doesn't exists.
2. Once the Terraform Cloud account created login to the Terraform Cloud portal with Username and Password.
3. Create an organization if you are new to Terraform cloud or use the existing organization.
4. Create a workspace while creating it choose API_driven workflow environment type and provide the workspace name.
5. Setup API_TOKEN for GitHub to Terraform Cloud connection setup
6. Go to workspace -> Settings -> Under the organizational settings blade choose API Tokens -> Under the API Tokens create Team Tokens -> Copy the Token.
7. Save the token as TF_API_TOKEN in GitHub Secrets.
8. Create terraform.tfvars variables under the Workspace
9. Service Principal login needs the following variables and get the values from the Azure App

          * subscription_id
          * client_id
          * client_secret
          * tenant_id
