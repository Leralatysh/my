
1. Create the directory and subdirectories:

\#project’s directory

_mkdir quickstart\docker_

\#code of the app

_mkdir quickstart\docker/application_

\#docker’s files

_mkdir quickstart\docker/docker_

\#application’s dockerfile

_mkdir quickstart\docker/docker/application_


2. Put the app into the _quickstart\docker/application_ directory:

_cd quickstart\docker/application_

_import http.server_

_import socketserver_

_PORT = 8000_

_Handler = http.server.SimpleHTTPRequestHandler_

_httpd = socketserver.TCPServer(("", PORT), Handler)_

_print("serving at port", PORT)_

_httpd.serve\forever()_


3. Get the application’s environment from the dockerhub:

3.1. Open the directory:

_cd quickstart\docker/docker/application_

3.2. Create a file named **dockerfile** with the following content:

\# Use base image from the registry

_FROM python:3.5_

\# Set the working directory to /app

_WORKDIR /app_

\# Copy the 'application' directory contents into the container at /app

_COPY ./application /app_

\# Make port 8000 available to the world outside this container

_EXPOSE 8000_

\# Execute 'python /app/application.py' when container launches

_CMD ["python", "/app/application.py"]_


4. Create an image:

_docker build . -f-docker/application/Dockerfile -t exampleapp_


5. Now it’s possible to see the list of images:

$ _docker images_





