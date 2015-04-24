Ansible Mesosphere
------------------

Install a Mesosphere stack on EC2 (Goal: Highly Available)

Install Ansible: 

    sudo easy_install pip
    sudo pip install boto --quiet --upgrade
    sudo pip install ansible --quiet --upgrade

Set your AWS Credentials:

    export ANSIBLE_HOST_KEY_CHECKING=False
    export EC2_REGION=eu-west-1
    export AWS_ACCESS_KEY=...
    export AWS_SECRET_KEY=...
    export AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY
    export AWS_SECRET_ACCESS_KEY=$AWS_SECRET_KEY

    
Create EC2 instances:

    PEM_NAME=vspiewak-xke CLIENT=xke ENV=dev ansible-playbook -i inventory/local playbooks/create-ec2.yml


Configure EC2 instances:

    PEM_PATH=~/.ssh/vspiewak-xke.pem CLIENT=xke ENV=dev ansible-playbook -i inventory/ec2.py playbooks/site.yml

    <or>

    PEM_PATH=~/.ssh/vspiewak-xke.pem CLIENT=xke ENV=dev ansible-playbook -i inventory/ec2.py playbooks/zookeeper.yml
    PEM_PATH=~/.ssh/vspiewak-xke.pem CLIENT=xke ENV=dev ansible-playbook -i inventory/ec2.py playbooks/mesos.yml
    PEM_PATH=~/.ssh/vspiewak-xke.pem CLIENT=xke ENV=dev ansible-playbook -i inventory/ec2.py playbooks/sensu.yml
    PEM_PATH=~/.ssh/vspiewak-xke.pem CLIENT=xke ENV=dev ansible-playbook -i inventory/ec2.py playbooks/gitlab.yml
