Create EC2 instances:

    PEM_NAME=vspiewak-xke ENV=dev ansible-playbook -i inventory/local playbooks/create-ec2.yml


Configure EC2 instances:

    PEM_PATH=~/.ssh/vspiewak-xke.pem ENV=dev ansible-playbook -i inventory/ec2.py playbooks/zookeeper.yml
    PEM_PATH=~/.ssh/vspiewak-xke.pem ENV=dev ansible-playbook -i inventory/ec2.py playbooks/mesos.yml
