
# How to install Datadog on AWS hosts with Ansible dynamic inventories
Ansible is an automation tool for provisioning, managing, and deploying infrastructure and applications. When building large-scale applications, Ansible enables users to manage and configure their infrastructure across platforms like AWS. Whether you rely on temporary or dedicated hosts, you can use Ansible to create a repeatable process for configuring them with the Datadog Agent. This process is especially useful if you need to monitor a dynamic inventory of resources (e.g., tagged EC2 instances) because Ansible can automatically manage these ephemeral resources.
## Setup Data-Dog For getting An AWS or any cloud resource [Click here](https://www.datadoghq.com/about/contact/)
## Check out How to get a Data-Dog Account and configure it for AWS [Click here]()
## Install the Datadog Agent Ansible role [Click here](https://github.com/professorxplorer/Set-upDataDogOnAnsibleDynamic-Inventory)
## Create a dynamic inventory of AWS EC2 instances in a single region [Click here]()
## create an Ansible playbook that automatically deploys the Agent to the dynamic inventory [Click here](https://github.com/professorxplorer/Ansible-Dynamic-Inventory)

# Get started with Ansible
There are a few prerequisites for getting started:
1. an AWS IAM user with access and secret key pairs and (at least) the AmazonEC2FullAccess permission policy to interact with the AWS API (you can configure using AWS configure checkout this [Click here]()
2. an up-to-date version (2.8 at the time of this publication) of Ansible on your host machine, where you will create the playbook and inventory file and configure the Datadog Agent
3. the ability to SSH into the EC2 instances you want to manage and monitor with Ansible and Datadog checkout this for SSH [Click here]()
### Solution
1. This repo I have added all the files ec2.py and ec2.ini
# Install the Datadog Agent Ansible role
1. In this repo we have already added ``` Datadog.datadog ``` role
2. if you would like to make your own run
``` ansible-galaxy install Datadog.datadog ```
# Make the main file to call it as main.yml
```main.yml
 - -
- name: Install Datadog Agent on servers in AWS
vars:
datadog_api_key: Your_Data-Dog-API_Key
datadog_config:
# tags:
# - env:dev
logs_enabled: true
process_config:
enabled: "true"
hosts: all
become: yes
user: ubuntu #Use the default login for the AWS image. Here we are using a ubuntu image.
roles:
- { role: Datadog.datadog, become: yes }
```
# Now simply run this ansible-playbook using
``` ansible-playbook -i ec2.py main.yml ```
## Authors
The module is maintained by [Professor Xplorer](https://professorexplorer.github.io/)
## License
Licensed. See [LICENSE]() for full details.