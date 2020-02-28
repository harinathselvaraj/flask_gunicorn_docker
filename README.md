# Creating a sample flask app with gunicorn in Docker
https://medium.com/@kmmanoj/deploying-a-scalable-flask-app-using-gunicorn-and-nginx-in-docker-part-1-3344f13c9649

## Creating basic Flask Docker
cd /current/folder/
docker build --tag flask_gunicorn_app:1.00 .
docker run --detach -p 8000:8000 flask_gunicorn_app:1.00             //first 8000 is accessed by localhost:8000
docker ps -a
a9c6aa79f7d0
Go to localhost:8000

## Stop the Docker container and Push to Docker Registry
docker exec -ti --user root a9c6aa79f7d0 bash
exit
docker tag flask_gunicorn_app:1.00 <docker_hub_url>/flask_gunicorn_app:1.00
docker push <docker_hub_url>/flask_gunicorn_app:1.00

## Deploy in Kubernetes directly for Load Balancing
Read Instructions on https://github.com/harinathselvaraj/ml_docker_kubernetes/

-- Not sure how to do NGINX Configuration setup. 
https://medium.com/@kmmanoj/deploying-a-scalable-flask-app-using-gunicorn-and-nginx-in-docker-part-2-fb33ec234113
## a) NGINX Configuration - Deploy in Docker Swarm (similar to Kubernetes) 
We are going to create 3 replicas of the flask_gunicorn_app, and make the load balancer handle the requests distribution.

## Python app
1) Clone a basic Flask app -- Interium Steps -- In future, we need to use the actual ML used during experimentation.

-- Go inside project folder 
virtualenv virt 
source virt/bin/activate 
pip install flask==1.0.2 requests flask_restful numpy pandas
pip install lightgbm
pip freeze > requirements.txt










