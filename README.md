Create EC2 instances:

    PEM_NAME=vspiewak-xke ansible-playbook -i inventory/local playbooks/create-ec2.yml


Configure EC2 instances:

    PEM_PATH=~/.ssh/vspiewak-xke.pem ansible-playbook -i inventory/ec2.py playbooks/mesos.yml
