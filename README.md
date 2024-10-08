# devops-tools-installation
DevOps Tools Installation Commands For Linux Instances

**First of all update the installed packages and package cache on your instance.**

sudo yum update -y

# Part 1 - Install DOCKER on Linux Instance #

sudo amazon-linux-extras install docker -y                     ## Install docker.

sudo systemctl start docker                                    ## Start docker service.

sudo systemctl enable docker                                   ## Enable docker service so that docker service can restart automatically after reboots#

sudo systemctl status docker                                   ## Check if the docker service is up and running.

newgrp docker                                                 ## Normally, the user needs to re-login into bash shell for the group docker to be effective, 
                                                                 but newgrp command can be used activate docker group for ec2-user, not to re-login into bash shell. 


docker version                                                 ## Check the docker version without sudo.   

docker info                                                    ## Check the docker info without sudo.



# Part 2 - Install TERRAFORM on Linux Instance #

sudo yum update -y                                            ## Always update the installed packages and package cache on your instance. 

sudo yum install -y yum-utils                                 ## Install yum-config-manager to manage your repositories.


## With command below use yum-config-manager to add the official HashiCorp Linux repository to the directory of /etc/yum.repos.d.##

sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo

sudo yum -y install terraform                                       ## Install Terraform.

terraform version                                                   ## Verify that the installation with seeing the version.

terraform -help                                                     ## List Terraform's available subcommands.



# Part 3 - Install JENKINS on Linux Instance #

sudo yum update -y                                                  ## Always update the installed packages and package cache on your instance.

sudo amazon-linux-extras install java-openjdk11 -y                  ## Install Java 11 openjdk Java Development Kit.

java -version                                                       ## Check the java version. 

## With below command add Jenkins repo to the yum repository.

sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo   


sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key      ## Import a key file from Jenkins-CI to enable installation from the package. 

sudo amazon-linux-extras install epel                               ## Enable the EPEL repository for Amazon EC2 instance.   

sudo yum install jenkins -y                                         ## Install Jenkins.

sudo systemctl start jenkins                                        ## Start Jenkins service.

sudo systemctl enable jenkins                                       ## Enable Jenkins service so that Jenkins service can restart automatically after reboots.

sudo systemctl status jenkins                                       ## Check if the Jenkins service is up and running.  

sudo cat /var/lib/jenkins/secrets/initialAdminPassword              ## Get the initial administrative password. 

## Open your browser, get your ec2 instance Public IPv4 DNS and paste it at address bar with 8080. "http://[ec2-public-dns-name]:8080"

## Enter the temporary password to unlock the Jenkins.

## Install suggested plugins.

## Create first admin user (call-jenkins:Call-jenkins1234).

## Check the URL, then save and finish the installation.



# Part 4 - Install ANSIBLE on Linux Instance #

sudo yum update -y

sudo amazon-linux-extras install ansible2

ansible --version



# Part 5 - Install PROMETHEUS on Linux Instance #

wget https://github.com/prometheus/prometheus/releases/download/v2.31.0-rc.0/prometheus-2.31.0-rc.0.linux-amd64.tar.gz

## Extract and run it with the following command: 

tar xvfz prometheus-*.tar.gz

## Check the basic prometheus configuration with the following commands: 

cd prometheus-*

cat prometheus.yml

## Start Prometheus: 

./prometheus --config.file=prometheus.yml

## Open the prometheus web UI from your browser:

http://<public ip of the ec2>:9090
