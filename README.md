Connect to AWS instance.

$ ssh -i "key.pem" ubuntu@ec2-your-instance-ip.compute.amazonaws.com

Create a password for the root user by running the following command.
$ sudo su
$ passwd root 

Install docker on Ubuntu 16.04.

$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
$ sudo apt-get update
$ apt-cache policy docker-ce
$ sudo apt-get install -y docker-ce
$ sudo systemctl status docker

Optional, add ubuntu user to docker group.

$ sudo usermod -aG docker ubuntu

Install docker-compose:

$ sudo curl -L https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose

Then clone project.

$ git clone https://github.com/sergey-rubtsov/docker-compose-scripts.git

Use docker-compose to start the containers.

$ docker-compose up
Restart the containers (after plugin upgrade or install for example).

$ docker-compose restart sonarqube
Analyse a project:

mvn sonar:sonar \
  -Dsonar.host.url=http://$(boot2docker ip):9000 \
  -Dsonar.jdbc.url=jdbc:postgresql://$(boot2docker ip)/sonar
