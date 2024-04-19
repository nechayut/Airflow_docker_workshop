# Airflow_docker_workshop

1.To deploy Airflow on Docker Compose, you should fetch docker-compose.yaml.

  curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.9.0/docker-compose.yaml'

2.On Linux, the quick-start needs to know your host user id and needs to have group id set to 0. Otherwise the files created in dags, logs and plugins will be created with root user ownership. You have to make sure to configure them for the docker-compose:

  mkdir -p ./dags ./logs ./plugins ./config
  echo -e "AIRFLOW_UID=$(id -u)" > .env

3. Create Dockerfile and requirement.txt (to install PyPi Packages).Replace section image: ${AIRFLOW_IMAGE_NAME:-apache/airflow:2.9.0} with build: .

4. On all operating systems, you need to run database migrations and create the first user account. To do this, run.

  docker compose up airflow-init

5.Now you can start all services:

  docker compose up

6.Put etl_workshop.py into dags folder

<img width="1196" alt="Screenshot 2567-04-19 at 22 33 28" src="https://github.com/nechayut/Airflow_docker_workshop/assets/101554284/d110d587-70dd-43d6-8771-1761e3fe2599">
