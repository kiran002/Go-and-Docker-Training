Now lets look at the Dockerfile, we create in order to containarize our server we built in the last task.

	FROM scratch
	COPY server /
	EXPOSE 8080
	ENTRYPOINT ["/server"]

*Before you get started, please make sure to copy the main.go from the Task-1 directory*

Scratch is the most basic image.It is empty,  literally 0 Bytes! Once we define the base image, we just copy the executable we had compiled earlier (although to be honest, we compile it a bit differently in order for it to work with scratch). Look at the command below

	CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o server .

Expose the port (8080), which we are listening to in our application and start our application. That's it!!

Now that we understand the dockerfile, lets see it in action

You can now create a docker image by running the following command,
	
	docker build -t "test" .

Using this above command, you are asking docker to a build an image called "test" based on the "Dockerfile" which is present in the current directory.

We have the image now, next step? Run it! you can do this by running the following command,
 
	docker run -d -p 8080:8080 test:latest


There are a couple of things going on in the above command, lets look into them. 

-d --> specifies that the container should run in a detached mode
-p --> Maps the port of the host to that of the container
test:latest --> the image we want the container to be based on and latest specifies the tag that we want it to use. 
