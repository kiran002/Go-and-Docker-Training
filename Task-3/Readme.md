# DockerHub

DockerHub, is a repository where all the docker images are saved. In future, if you want to run your server on a different machine or on a friends computer, you dont have to run build your "hello-world" server, create the Dockerfile and then run it. You can simply pull your image hosted on DockerHub and run it.

*Note: If you dont want to share your docker image publically or host it on third party websites. Please feel free to skip this part*

## Step-1: Create a docker hub account

## Step-2: Create a docker hub repository, called hello-world

## Step-3: Build your docker image, with the appropriate tag

	docker build -t "<user-name>/hello-world" .

## Step-4: Login to your dockerhub using the cli

	docker login

and enter your credentials, when prompted.

## Step-5: Push your container to DockerHub

	docker push <user-name>/hello-world


Congratulations! Your first docker image is now hosted on dockerhub and accessible to the entire world! 

## Step-6: (Optional) Pull your image from the DockerHub

Want to check it out?Sure, but before lets delete the locally created image. You can do it by running the following command,

	docker rmi <user-name>/hello-world

rmi--> stands for remove image

Now that its deleted, lets pull the image from DockerHub. You can do this simply by running the following command,

	docker run -d -p 8080:8080 <user-name>/hello-world


and Voila! you can see this pull's the image directly from the DockerHub!




