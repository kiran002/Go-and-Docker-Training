## Docker Swarm

By now, you should already know

1. How to create a docker image
2. How to run a container instance based on your image
3. How to push your image to docker hub

So whats next? Next is Docker Swarm, which facilitates container orchestration. You might have heard about Kubernetes (K8's), K8's is also a container orchestration application, we will cover K8's in the next chapter. But to get started and understand, what does container orchestration actually mean? We will look into Docker Swarm, which is perfect for getting started!

Before we get started, why do we need container orchestration?

The answer is quite simple, Let us assume you have a cluster of nodes running multiple different applications. Imagine the following scenarios,

1. What if one of the node fails? (what will happen to the containers that where running on the node?

2. What if containers fail or crash? How could you monitor them? 

3. How would you release a new version, without having any down time?

4. How could different applications, talk to each other?

5. How could you scale your services? 


The above reasons are some of the reasons why, you would move to use a container orchestration tool such as Swarm or K8's.


Let us now look at swarm in action,


## Initializing a swarm

	docker swarm init

## Create hello-world service

	docker service create --name "hello-world" --publish 8080:8080 kiran002/hello-world
	

Now if you open localhost:8080, in your browser. You sould already see the familiar "hello-world" message.

## What is a service?

How is having a service running different from a container we had earlier? The difference is not so obvious with our example, but in order to showcase it. Lets perform a small test, run the following command which will kill al running containers

	docker kill $(docker ps --format {{.ID}})

After that, if you do a docker ps. For an instance you will see that no container is running. But soon after you will notice a new container being created. What exactly happened? Docker swarm realized that one of the containers, which was supposed to be running was killed. So it created a new instance of it to replace the container which was killed

## Scaling a service

One of the other features of using a swarm service is scaling. Imagine you want to run 5 instances of your containers. All of whom are listening to the port 8080 and return "hello-world", this is very easy with the swarm service API.

	docker service scale hello-world=5

Thats it! Now you have 5 instances of your application running! Based on what you want to do you can either scale up or scale down.

## Logs?

Now we have 5 different instances of our application running, checking the logs of our containers is also quite straightforward with the swarm api. You can just run the following command,
	
	docker service logs hello-world


## Deleting a service

Just as we add new services, from time to time we will also delete them. This is achieve by running the following command

	docker service rm hello-world

Now if you run,
	
	docker ps

you will realize that no containers are running and everything was indeed stopped.


## Portainer : GUI for monitoring Swarm

In order to manage the swarm with a GUI, you can start portainer with the following command

	docker service create --name portainer  --constraint 'node.role == manager'  --mount type=bind,src=//var/run/docker.sock,dst=/var/run/docker.sock --publish 9000:9000 portainer/portainer

You can then open the URL, localhost:9000 and try to repeat what we did up until now using the GUI.


## Cleaning up

Once you are done, you can clean your envrionment up by running

	docker swarm leave --force

Next stop, Kubernetes!
