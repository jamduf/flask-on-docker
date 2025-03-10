# Flask on Docker

## i. Overview
This repo contains a Flask web application that runs using Docker and nginx. The app allows you to upload small-sized images and gifs (under 1 MB), which are stored and displayed via Flask. This project shows a containerized web app that can handle file uploads, while maintaining a seperation between web and proxy.

### Example
![Upload Demo](flaskdockerexample.gif)  

## Build Instructions
### 1: Install Docker and Docker Compose if you have not already

### 2: Clone the Repo:
```sh
   git clone https://github.com/jamduf/flask-on-docker.git
   cd flask-on-docker
```
### 3: Set up Environment Variables
Add a file called `.env.dev` in the root file.

Add the environment variables:
```sh
FLASK_APP=project/__init__.py
FLASK_DEBUG=1
DATABASE_URL=postgresql://hello_flask:hello_flask@db:5432/hello_flask_dev
SQL_HOST=db
SQL_PORT=5432
DATABASE=postgres
```

### 4: Build and Start:
run this command: 
```sh
docker compose up --build
```

Open http://localhost:1345/upload in your browser, and upload an image to test!

Then, you can view the image by going to http://localhost:1345/media/[your_image.filetype]

To shut down, use:
```sh
docker compose down
```

## Production Mode
If using for production mode, create a file called `.env.prod` in the root file. 

Add the environment variables:
```sh
FLASK_APP=project/__init__.py
FLASK_DEBUG=0
DATABASE_URL=postgresql://hello_flask:hello_flask_prod@db:5432/hello_flask_prod
SQL_HOST=db
SQL_PORT=5432
DATABASE=hello_flask_prod
```

to run the app, use 
```sh
docker compose -f docker-compose.prod.yml up --build
```

