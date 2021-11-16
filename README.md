# flask-11-2021

## https://runnable.com/docker/python/dockerize-your-flask-application
- flask_web app directory
- testing docker implementation

## https://codefresh.io/docker-tutorial/hello-whale-getting-started-docker-flask/
- app directory

## https://www.tutorialspoint.com/build-and-deploy-a-flask-application-inside-docker
- flask_project
#  File "/usr/src/app/app.py", line 11
#    return “Welcome to TutorialsPoint”
#           ^
# SyntaxError: invalid character '“' (U+201C)


## https://medium.com/swlh/build-your-first-automated-test-integration-with-pytest-jenkins-and-docker-ec738ec43955
- pytest usage
- Multiple Jenkins/Docker
- Important commands
- docker build -t jenkins-docker-image -f JenkinsDockerfile .
- docker run -d -p 8080:8080 --name jenkins-docker-container -v /var/run/docker.sock:/var/run/docker.sock jenkins-docker
- Verify Jenkins Docker Container is running with [ docker ps -a ]
- Grab jenkins pw -> docker exec -it jenkins-docker-container cat var/jenkins_home/secrets/initialAdminPassword
- https://github.com/viseth89/python-test-calculator