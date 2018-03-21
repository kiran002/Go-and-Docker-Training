In the main.go, we have our very simple hello world server. This is listening for requests on port 8080 and always returns "hello world"

The main method is quite straight forward, we define a default handle method called handler and bind our application to the port 8080,

	func main() {
		http.HandleFunc("/", handler)
		log.Fatal(http.ListenAndServe(":8080", nil))
	}

The handle function is also quite straightforward as well, it just writes "hello world" string back as a response

	func handler(w http.ResponseWriter, r *http.Request) {
		fmt.Fprintf(w, "Hello world!")
	}

you can compile this program by running,

	go build -o server

and run the executable simply by running 

	./server

If you now open localhost:8080/ , you will see that in indeed returns "Hello world!"


Hurray! We have a very simple server running and now lets put run it in docker. Next task we will create a dockerfile and see how we can run the same on docker.
