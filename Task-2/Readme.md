Now lets look at the Dockerfile, we create in order to containarize our server we built in the last task.

	FROM scratch
	COPY server /
	EXPOSE 8080
	ENTRYPOINT ["/server"]

Scratch is the most basic image.It is empty,  literally 0 Bytes! Once we define the base image, we just copy the executable we had compiled earlier (although to be honest, we compile it a bit differently in order for it to work with scratch). Look at the command below

	CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o server .

Expose the port (8080), which we are listening to in our application and start our application. That's it!!

Now that we understand the dockerfile, lets see it in action

Creating a docker Image,
	
	docker build -t "test" .

Run it 
	docker run -d -p 8080:8080 test:latest
