## Part 1 Tasks

### 1.1 Getting started

Start 3 containers from image that does not automatically exit, such as nginx, detached.
Stop 2 of the containers leaving 1 up.
Submitting the output for docker ps -a is enough to prove this exercise has been done.

### 1.2 Cleanup

We’ve left containers and a image that won’t be used anymore and are taking space, as docker ps -as and docker images will reveal.
Clean the docker daemon from all images and containers.
Submit the output for docker ps -a and docker images

### 1.3 Hello Docker Hub

Start image devopsdockeruh/pull_exercise with flags -it like so: docker run -it devopsdockeruh/pull_exercise. It will wait for your input. 
Navigate through docker hub to find the docs and Dockerfile that was used to create the image.
Read the Dockerfile and/or docs to learn what input will get the application to answer a “secret message”.
Submit the secret message and command(s) given to get it as your answer.

### 1.4
Now that we’ve warmed up it’s time to get inside a container while it’s running!
Start image devopsdockeruh/exec_bash_exercise, it will start a container with clock-like features and create a log. 
Go inside the container and use tail -f ./logs.txt to follow the logs. Every 15 seconds the clock will send you a “secret message”.
Submit the secret message and command(s) given as your answer.

### 1.5
Start a ubuntu image with the process sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
You will notice that a few things required for proper execution are missing. Be sure to remind yourself which flags to use so that the read actually waits for input.
Note also that curl is NOT installed in the container yet. You will have to install it from inside of the container.
Test inputting helsinki.fi into the application. It should respond with something like

<html>
<head>
  <title>301 Moved Permanently</title>
</head>
<body>
  <h1>Moved Permanently</h1>
  <p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body>
</html>
This time return the command you used to start process and the command(s) you used to fix the ensuing problems.

### 1.6
Create a Dockerfile that starts with FROM devopsdockeruh/overwrite_cmd_exercise. Add a CMD line to the Dockerfile.
The developer has poorly documented how the application works. Nevertheless once you will execute an application (run a container from an image) you will have some clues on how it works. Your task is to run an application so that it will simulate a clock functionality.
When you will build an image tag it as “docker-clock” so that docker run docker-clock starts the application.
Return both Dockerfile(s) and the command you used to run the container(s)

### 1.7
Now that we know how to create and build Dockerfiles we can improve previous works.
Create a Dockerfile for a new image that starts from ubuntu:16.04.
Make a script file on you local machine with such content as echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;. Transfer this file to an image and run it inside the container using CMD. Build the image with tag “curler”.
Run command docker run [options] curler (with correct flags again, as in 1.5) and input helsinki.fi into it. Output should match the 1.5 one.
Return both Dockerfile(s) and the command you used to run the container(s)

### 1.8
In this exercise we won’t create a new Dockerfile. Image devopsdockeruh/first_volume_exercise has instructions to create a log into /usr/app/logs.txt. Start the container with bind mount so that the logs are created into your filesystem.
Submit your used commands for this exercise.

### 1.9
In this exercise we won’t create a new Dockerfile. Image devopsdockeruh/ports_exercise will start a web service in port 80. Use -p flag to access the contents with your browser.
Submit your used commands for this exercise.

### 1.10
A good developer creates well written READMEs that can be used to create Dockerfiles with ease.
Clone, fork or download a project from https://github.com/docker-hy/frontend-example-docker.
Create a Dockerfile for the project and give a command so that the project runs in a docker container with port 5000 exposed and published so when you start the container and navigate to http://localhost:5000 you will see message if you’re successful.
Submit the Dockerfile.
As in other exercises, do not alter the code of the project
TIP: The project has install instructions in README.
TIP: Note that the app starts to accept connections when “Accepting connections at http://localhost:5000” has been printed to the screen, this takes a few seconds
TIP: You do not have to install anything new outside containers.

### 1.11
Clone, fork or download a project from https://github.com/docker-hy/backend-example-docker.
Create a Dockerfile for the project and give a command so that the project runs in a docker container with port 8000 exposed and published so when you start the container and navigate to http://localhost:8000 you will generate a message in logs.txt in the working directory.
Create a volume for the logs.txt so that when the application is shut down the logs are not destroyed. And when restarted it continues to write into the same logs.txt.
Submit the Dockerfile and the command used.
Do not alter the code of the project

### 1.12
Start both frontend-example and backend-example with correct ports exposed and add ENV to Dockerfile with necessary information from both READMEs (front,back).
Ignore the backend configurations until frontend sends requests to _backend_url_/ping when you press the button.
You know that the configuration is ready when the button for 1.12 of frontend-example responds and turns green.
Do not alter the code of either project
Submit the edited Dockerfiles and commands used to run.
The frontend will first talk to your browser. Then the code will be executed from your browser and that will send a message to backend.
TIP: When configuring web applications keep browser developer console ALWAYS open, F12 or cmd+shift+I when the browser window is open. Information about configuring cross origin requests is in README of the backend project.
TIP: Developer console has multiple views, most important ones are Console and Network. Exploring the Network tab can give you a lot of information on where messages are being sent and what is received as response!

### 1.13
Lets create a Dockerfile for a Java Spring project: github page
The setup should be straightforward with the README instructions. Tips to get you started:
Use openjdk image FROM openjdk:_tag_ to get java instead of installing it manually. Pick the tag by using the README and dockerhub page.
You’ve completed the exercise when you see a ‘Success’ message in your browser.

### 1.14
Lets create a Dockerfile for a rails project: github page.
Again we can take a look at the README for the project to see the installation instructions. Tips to get you started:
Use Ruby image FROM ruby:_tag_ to easily get most of what you’ll need at the beginning. Pick the tag by using the README and dockerhub page.
If you want you can make small edits to the program if you get stuck and google doesn’t help you configure the setup. If you did, explain the edits with your submission of the Dockerfile.
You’ve completed the exercise when the application works in your browser.

### 1.15
Create Dockerfile for an application or any other dockerised project in any of your own repositories and publish it to Docker Hub. This can be any project except clones / forks of backend-example or frontend-example.
For this exercise to be complete you have to provide the link to the project in docker hub, make sure you at least have a basic description and instructions for how to run the application in a README that’s available through your submission.

### 1.16
Pushing to heroku happens in a same way. A project has already been prepared at devopsdockeruh/heroku-example so lets pull that first. Note that the image of the project is quite large.
Go to https://www.heroku.com/ and create a new app there and install heroku CLI. You can find additional instructions from Deploy tab under Container Registry. Tag the pulled image as registry.heroku.com/_app_/_process-type_, process-type can be web for this exercise. The app should be your project name in heroku.
Then push the image to heroku with docker push registry.heroku.com/_app_/web and release it using the heroku CLI: heroku container:release web (you might need to login first: heroku container:login)
For this exercise return the url in which the released application is.
You could also use the heroku CLI to build and push, but since we didn’t want to build anything this time it was easier to just tag the image.

### 1.17
Create an image that contains your favorite programming environment in it’s entirety.
This means that a computer that only has docker can use the image to start a container which contains all the tools and libraries. Excluding IDE / Editor. The environment can be partially used by running commands manually inside the container.
Explain what you created and publish it to Docker Hub.

