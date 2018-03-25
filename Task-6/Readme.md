Now that you have seen a bit of Swarm. Lets move on to the next beast, Kubernetes! Kubernetes can handle production workloads across clusters of machines and is the current defacto standard for container orchestration. In order to go on with this task, you need to have installed minikube and kubectl. 

Having said that, Kubernetes is quite complicated. Lets try to replicate, what we did with swarm in Kubernetes


## Start your minikube
	
	minikube start

when the minikube is started, you should see a message that says minikube was successfully started and your kubectl has been configured.

## Deploy your application

	kubectl run hello-world --image=<user-name>/hello-world --port=8080 --replicas=2

Replace your docker-hub username and run the command. You will get a message that the deployment was created.


## Accessing your application

After you have run the above command and tried to access it over localhost:8080, you see that nothing is running there. So what happened? lets check if the pods were infact created. you can do this with

	kubectl get pods

Everything seems to be fine, so why are you not able to access it? This is because the container is running in its own cluster. Right now its not possible to access it, because we have not specified any external route through which we can access the pods. So what next? We can connect to our cluster, by running the following command

	kubectl proxy

Now to access our pod, please replace the <pod-name> with the pod name you get when you run `kubectl get pods` command

	http://localhost:8001/api/v1/proxy/namespaces/default/pods/<pod-name>/


You will see, you now see the very familiar, "hello world!" message! What did you just do? You access your pod, over the k8's api server. However this is not very reliable, because the pod's name is not static, it changes all the time. So how do we overcome this problem? Services!


## Exposing your application with a service

	kubectl expose deployment hello-world --type=NodePort --name=first-service


You can access the endpoint with, 
	
	minikube service first-service








