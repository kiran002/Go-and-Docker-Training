We have now created a dockerfile, now lets get started

	CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o server .
	docker build -t "test" .
	docker run -d -p 8080:8080 test:latest
