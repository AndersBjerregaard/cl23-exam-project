# Running the project with the docker compose file

Since the docker compose file is dependent on the frontend- and backend application existing as images already. It is paramount that these images are built before attempting to run the services in tandem.

### Build image for frontend application
Change directory into the parent directory of the project, default name: "cl23-exam-project".
From there:
```bash
docker build -t cl-exam-frontend ./frontend
```

Make sure you tag the image with the correct name, as the docker compose file is reliant on this property.

### Build image for backend application
Change directory into the parent directory of the project, default name: "cl23-exam-project".
From there:
```bash
docker build -t cl-exam-backend ./backend
```

### Running the application
After the images have been built, from the same parent directory as before:
```bash
docker compose up -d
```

You should see the services running in tandem either through your terminal `docker ps` or in Docker Desktop.

# Running the project orchestrated by a Docker Swarm

### Build image for frontend application
Change directory into the parent directory of the project, default name: "cl23-exam-project".
From there:
```bash
docker build -t cl-exam-frontend ./frontend
```

Make sure you tag the image with the correct name, as the docker compose file is reliant on this property.

### Build image for backend application
Change directory into the parent directory of the project, default name: "cl23-exam-project".
From there:
```bash
docker build -t cl-exam-backend ./backend
```

After the images have been built, from the same parent directory as before:
```bash
docker swarm init
docker stack deploy --compose-file docker-compose.yaml zay_stack
```

Keep in mind that without further configuration this will orchestrate your current machine as the Docker Swarm host and no further nodes other than the machine itself. However, you should see the three services corresponding to the frontend- and backend application, as well a the database, running and restarting if being stopped.
