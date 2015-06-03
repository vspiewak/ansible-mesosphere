Ansible Mesosphere
==================

Install a Mesosphere stack on EC2 :

  * Zookeeper cluster
  * Mesos cluster
  * Marathon
  * Sensu for alerting/monitoring
  * GitLab for hosting code


Install Ansible
---------------
(On OSX for instance...)

    sudo easy_install pip
    sudo pip install boto --quiet --upgrade
    sudo pip install ansible --quiet --upgrade


Configure your AWS Credentials
------------------------------

    export ANSIBLE_HOST_KEY_CHECKING=False
    export EC2_REGION=eu-west-1
    export AWS_ACCESS_KEY=...
    export AWS_SECRET_KEY=...
    export AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY
    export AWS_SECRET_ACCESS_KEY=$AWS_SECRET_KEY


Configure your EC2 pem file
---------------------------

    export PEM_NAME=<aws_pem_name>
    export PEM_PATH=~/.ssh/<aws_pem_name>.pem


Configure EC2 instances tags
----------------------------

    export CLIENT=company
    export ENV=dev


Create EC2 instances
--------------------

    ansible-playbook -i inventory/local playbooks/create-ec2.yml


Configure EC2 instances
-----------------------

    ansible-playbook -i inventory/ec2.py playbooks/site.yml

    <or>

    ansible-playbook -i inventory/ec2.py playbooks/zookeeper.yml
    ansible-playbook -i inventory/ec2.py playbooks/mesos.yml
    ansible-playbook -i inventory/ec2.py playbooks/marathon.yml
    ansible-playbook -i inventory/ec2.py playbooks/gitlab.yml
    ansible-playbook -i inventory/ec2.py playbooks/sensu.yml


You can browse
--------------

  * `http://<mesos_master_url>:5050`
  * `http://<marathon_url>:8080`
  * `http://<sensu_url>:3000`
  * `http://<gitlab_url>`


Deploy an app on marathon
-------------------------

    curl -XPOST -H 'Content-Type: application/json' http://<marathon_url>:8080/v2/apps -d @sample.json


Terminate EC2 instances
-----------------------

    ansible-playbook -i inventory/ec2.py playbooks/terminate-ec2.yml



TODO
----

  * Configure Sensu alerting (via mail)
  * Configure Sensu checks for docker
  * Configure Marathon in HA mode
  * Configure Chronos (?)
  * Install Chaos Monkeys
