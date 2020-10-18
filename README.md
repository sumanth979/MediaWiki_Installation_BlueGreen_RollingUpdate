# ThoughtWorksLab
ThoughtWorks Lab Exercise

## Problem Statement
We want to automate the deployment of MediaWiki using.
* Kubernetes with Helm Chart/ any equivalent automation
* CFT with Any Configuration Management Tool (Only for AWS). If any 
* Terraform with any Configuration Management tool integrated.
--
Choose only one of your comfort.
* The above automation should support CI/CD practices of chosen deployment style like Rolling Update or BlueGreen Deployment. (Optional)

## Technologies Used
This Technologies used in this deployment is
* Yaml Scripting
* Python
* Shell Scripting
* Cloud Formation Template
* Ansible Playbooks

## Deployment Templates Available
* Blue-Green Deployment
* Rolling Update Template

## Deployment Steps

### File Details
* blueGreen.yaml                 - Cloud Formation template for blue green deployment.
* rollingUpdate.yaml             - Cloud Formation template for rolling deployment.
* parameters.json                - The parameters file for blue green deployment.
* mediawikiInstallationSteps.txt - Manual steps for mediawiki installation.
* dynamicInventory.py            - To create dynamic Inventory based on the ec2 tags.
* playbook.yaml                  - Ansible playbook for mediaWiki installation.
* seup.sh                        - Setup file for deployment.

### Deployment Process

#### Running in a single Step
* To complete the deployment in a single step
```
sh setup.sh
```

#### Running Each File Seperately
* To Deploy the Cloud Formation Stack using cli
```
echo "Creating the stack"
aws cloudformation create-stack --stack-name demo-stack --template-body blueGreen.yaml --parameters parameters.json
```

* To Create the inventory file dynamically
```
echo "Dynamically create the invertory file for ansible"
python3 dynamicInventory.py demo-stack us-east-1
```

* To install mediaWiki using ansible.
```
echo "Run Ansible Playbook to deploy mediaWiki"
ansible-playbook playbook.yaml -i invertory.txt
```

## Outputs


## Architecture
### Blue Green Mode
<img src="https://github.com/sumanth979/ThoughtWorksLab/blob/main/output/blue-green.png" alt="blue-green">

### Rolling Update Mode

<img src="https://github.com/sumanth979/ThoughtWorksLab/blob/main/output/rolling.png" alt="rolling">


