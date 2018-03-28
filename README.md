Use docker-compose to start the containers.

$ docker-compose up
Restart the containers (after plugin upgrade or install for example).

$ docker-compose restart sonarqube
Analyse a project:

mvn sonar:sonar \
  -Dsonar.host.url=http://$(boot2docker ip):9000 \
  -Dsonar.jdbc.url=jdbc:postgresql://$(boot2docker ip)/sonar