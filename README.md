On this page:

* [Prerequisites](https://bitbucket.org/teamshowcaser/devops/overview#prerequisites)
 * [Unzip](https://bitbucket.org/teamshowcaser/devops/overview#unzip)
 * [Terraform installation](https://bitbucket.org/teamshowcaser/devops/overview#terraform-installation)
   * [Download Terraform](https://bitbucket.org/teamshowcaser/devops/overview#download-terraform)
   * [Install Terraform](https://bitbucket.org/teamshowcaser/devops/overview#install-terraform)
 * [jq](https://bitbucket.org/teamshowcaser/devops/overview#jq)
 * [zip](https://bitbucket.org/teamshowcaser/devops/overview#zip)
* [Run script](https://bitbucket.org/teamshowcaser/devops/overview#run-script)
* [Notes](https://bitbucket.org/teamshowcaser/devops/overview#notes)

## Prerequisites

### Terraform installation

#### Unzip
More Details [unzip](http://www.brocade.com/content/html/en/software-installation-guide/SDN-Controller-2.1.0-Software-Installation/GUID-0E81C58A-6F32-4862-9B0C-84F2DC8BA238.html)
Ubuntu:-
`sudo apt install unzip -y`
CentOS:-
`sudo yum install unzip -y `

#### Download Terraform

latest release from HashiCorp’s Release page. Go to the URL below in your browser
https://releases.hashicorp.com/terraform/

#### Install Terraform
Change directory to your downloads directory.
`cd ~/Downloads`

Unzip the archive.
`unzip terraform_0.10.8_linux_amd64.zip`

This will extract a terraform file into the Downloads directory. Now you need to move it to your path.
`sudo mv terraform /usr/local/bin`

Add your path in ~/.bash_profile
`export PATH=$PATH:/usr/local/bin/`

That’s all. Now try running it.
`terraform --version`

### JQ
jq is command-line JSON processor
More details: [JQ](https://stedolan.github.io/jq/download/)
`sudo apt-get update sudo apt-get install jq`

### Zip
More detail: [how to install zip](https://www.digitalocean.com/community/questions/how-to-install-zip-in-ubuntu)
`sudo apt-get install zip`

### n2
Install n2 for node versioning
More detail: [n2](https://www.npmjs.com/package/n2)
npm install -g n

## Generate session
Generate session in terminal before run terraform scripts
`source session.sh <SSO_ACCOUNT_ID> <AWS_SESSION_NAME> <AWS_USER> <ROLE_ARN> <ACCOUNT_ID> <MFA_TOKEN>`

## Run script
- Add config.auto.tfvars file in environment folder which you want to deploy
- Update variables in config.auto.tfvars
- Run shell script file from env folder using:
`sh server.sh`

## Notes


While you run terraform script, It will ask for deployment version. Enter the Deployment version as shown in example below. Deployment version will append with zip file name like this *“auth-lamnda-0.0.1.zip”* . Now terraform will upload this zip file to s3 bucket. By doing this we will always  have backup of older node versions. We need to add updated version (naming convention for Version is company specific)  in every terraform cycle so that we can get updated code in NodeJs, React front and React admin


> var.deployment_version
> Enter a value: |
