FROM python:3.10-slim-buster

# inside the container, create new dir backend-flask
WORKDIR /backend-flask

# copy requirements.txt from outside the container to inside container
COPY  requirements.txt requirements.txt
# inside container install python lib for api
RUN pip3 install -r requirements.txt

#copy everything from outside container to inside container
#first period is outside container /backend-flask
#second period is inside container /backend-flask
COPY . .
#env variable inside container, remain set when container is running
ENV FLASK_ENV=development
#
EXPOSE ${PORT}
#CMD (command) to run flask inside container to exposed port
# to run locally, need env variables
# export FRONTEND_URL="*"
# export BACKEND_URL="*"
# go to api/activities/home
CMD [ "python3", "-m", "flask", "run", "--host=0.0.0.0", "--port=4567"]
#build container in main dir with: docker build -t backend-flask ./backend-flask 
#run with: docker run --rm -p 4567:4567 -it backend-flask
#run with environment vars FRONTEND_URL="*" BACKEND-URL="*" docker run --rm -p 4567:4567 -it backend-flask
#run in background with 
#docker container run --rm -p 4567:4567 -d backend-flask
#docker run --rm -p 4567:4567 -it -e FRONTEND_URL='*' -e BACKEND_URL='*' -d backend-flask
#return container id into an env var
#CONTAINER_ID=$(docker run -rm -p 4567:4567 -d backend-flask)