Create EC2 instances:

    PEM_NAME=vspiewak-xke CLIENT=xke ENV=dev ansible-playbook -i inventory/local playbooks/create-ec2.yml


Configure EC2 instances:

    PEM_PATH=~/.ssh/vspiewak-xke.pem CLIENT=xke ENV=dev ansible-playbook -i inventory/ec2.py playbooks/site.yml
    
    PEM_PATH=~/.ssh/vspiewak-xke.pem CLIENT=xke ENV=dev ansible-playbook -i inventory/ec2.py playbooks/zookeeper.yml
    PEM_PATH=~/.ssh/vspiewak-xke.pem CLIENT=xke ENV=dev ansible-playbook -i inventory/ec2.py playbooks/mesos.yml
