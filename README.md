1. Create the directory and subdirectories:
#project’s directory

mkdir quickstart\docker

#code of the app

mkdir quickstart\docker/application

#docker’s files

mkdir quickstart\docker/docker

#application’s dockerfile

mkdir quickstart\docker/docker/application

2. Put the app into the quickstart\docker/application directory:
cd quickstart\docker/application

import http.server

import socketserver

PORT = 8000

Handler = http.server.SimpleHTTPRequestHandler

httpd = socketserver.TCPServer(("", PORT), Handler)

print("serving at port", PORT)

httpd.serve\forever()

3. Get the application’s environment from the dockerhub:
3.1. Open the directory:

cd quickstart\docker/docker/application

3.2. Create a file named dockerfile with the following content:

# Use base image from the registry

FROM python:3.5

# Set the working directory to /app

WORKDIR /app

# Copy the 'application' directory contents into the container at /app

COPY ./application /app

# Make port 8000 available to the world outside this container

EXPOSE 8000

# Execute 'python /app/application.py' when container launches

CMD ["python", "/app/application.py"]

4. Create an image:
docker build . -f-docker/application/Dockerfile -t exampleapp

5. Now it’s possible to see the list of images:
$ docker images
