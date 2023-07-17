Here's a step-by-step guide on how to install and run Jenkins with Docker Compose

**Prerequisites:**

- Docker and Docker Compose installed on your system
- Access to Docker Hub to download the latest Jenkins images

**Running Jenkins With Docker Compose:**

1. Create a directory named `jenkins_compose` and create a file named `docker-compose.yaml` with these contents:
```yml
version: '3.8'
services:
  jenkins:
    image: jenkins/jenkins:lts
    privileged: true
    user: root
    ports:
      - 8080:8080
      - 50000:50000
    container_name: jenkins
    volumes:
      - /home/${myname}/jenkins_compose/jenkins_configuration:/var/jenkins_home
      - /var/run/docker.sock:/var/run/docker.sock
```

Replace `/home/${myname}` with your user’s home directory or the path you created the new directory in.

2. Run your Jenkins controller by executing `docker-compose up -d` in the directory where you placed `docker-compose.yaml`.
    
3. Open a web browser and navigate to port 8080 on your host system. You’ll see the unlock page.
    
4. Retrieve the initial password from the Docker log by running `docker logs jenkins | less` and look for a block enclosed with six lines of asterisks. Enter this password in the unlock page and click Continue.
    
5. Select "Install Suggested Plugins" on the next page. When Jenkins finishes, it will prompt you for a new admin user and password. Enter a user name and password and click "Save and Continue".
    
6. The next page gives you a chance to change the host name of your controller. For this tutorial, you can accept the default and click "Save and Finish".
    

**Adding a Jenkins Agent With Docker Compose:**

1. Generate an SSH key using `ssh-keygen` to create a key. This key will allow the controller to access the agent via SSH.
    
2. Add the generated private key to Jenkins credentials.
    
3. Add a new service to your `docker-compose.yaml`:
    
```yml
agent:
  image: jenkins/ssh-agent:jdk11
  privileged: true
  user: root
  container_name: agent
  expose:
    - 22
  environment:
    - JENKINS_AGENT_SSH_PUBKEY=<your-public-key>
```

Replace `<your-public-key>` with your generated public key.

4. Run `docker-compose down` and then `docker-compose up -d` to start everything up.
    
5. In Jenkins, click "Manage Jenkins", and select "Manage Nodes and Clouds". Click "New Node" and define your Jenkins agent.
    
6. At the top of the form, give your agent a name and set the Remote root directory to `/home/jenkins/agent`.
    
7. Under "Launch method", select "Launch agents via SSH". For Host, enter `agent`. Each container can reach the others by using their container names as hostnames.
    
8. Next, click the dropdown under Credentials and select the one you just defined.
    
9. Under "Host Key Verification Strategy", select "Non verifying Verification Strategy". Click "Advanced" on the right.
    
10. Set the JavaPath to `/usr/local/openjdk-11/bin/java`. Click "Save" at the bottom.
    

Now you should have a Jenkins controller and agent running with Docker Compose.