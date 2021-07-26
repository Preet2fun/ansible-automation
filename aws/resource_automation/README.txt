step 1 : Create SSH keys to connect to the EC2 instance after provisioning
ssh-keygen -t rsa -b 4096 -f ~/.ssh/my_aws

step 2: Create Ansible Vault file to store the AWS Access and Secret keys.
ansible-vault create group_vars/all/pass.yml

step3 : Edit the pass.yml file and create the keys global constants
Create the variables ec2_access_key and ec2_secret_key and set the values gathered after user creation (IAM).
ansible-vault edit group_vars/all/pass.yml 
Vault password:
ec2_access_key: AAAAAAAAAAAAAABBBBBBBBBBBB                                      
ec2_secret_key: afjdfadgf$fgajk5ragesfjgjsfdbtirhf

for ssh into VM use below command
ssh -i /root/.ssh/my_aws ubuntu@ec2-35-153-79-17.compute-1.amazonaws.com

command for playbook run
ansible-playbook -i hosts playbook.yaml --tag=create_ec2 --ask-vault-pass