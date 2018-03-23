As we saw in the previous task, we can run contains using the docker run command. However, when you want to share and distribute this command it can become quite complex, hard to read and maintain. Hence we use docker-compose to maintain all the information required inorder to start your container in a yaml file. As seen below.

Before we get started, make sure you have installed docker-compose.


## docker-compose.yml
	version: '3'
	services:
	  hello-world:
	    ports:
	     - "8080:8080"
	    image: "kiran002/hello-world"


The compose file itself is quite self explanatory. You can start it by running the following command,


	docker-compose up -d


