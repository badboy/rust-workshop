# Rust workshop

This workshop is aimed at beginners of the Rust programming language who however have experience in other languages. We will build a *multithreaded webserver*.

## [Step 1](step1/): Creating a new project

Setup Rust and an empty `Hello World` project.
Create a new project using `cargo` and ensure that you can compile and run the `Hello World` example.

## [Step 2](step2/): Single-threaded server

Listen to incoming requests, handling them one at a time.

Task: You should create a simple server listening on a TCP port. When accepting a new connection, it reads incoming data and discard it. It then writes a simple HTTP response to the client and then close the connection. It continues to listen for new connections.

* Take a look at `TcpListener` in the documentation and base your code on the provided example
* Send a HTTP response like `"HTTP/1.1 200 OK\r\n\r\nHello strangers!"`
* Code can be built using `cargo build`
* To run the server use `cargo run`
* To test the server send a request using curl: `curl http://localhost:7200`, or use your web browser.

## [Step 3](step3/): Multi-threaded server

Adding some simple multithreading into the equation

Task: Turn the previous single-threaded server into a multi-threaded one. For every incoming connection spawn a new thread and handle the connection in that thread as before, reading and discarding data and sending a simple HTTP response.

* Look at the documentation for `std::thread`

Extended Task: Implement a connection counter. For every incoming connection increase the counter and reply with the total number of connections seen.

Helpful things:

* `std::sync::Mutex`
* `std::sync::Arc`

## [Step 4](step4/): Multi-threaded server with thread pool

Using a threadpool for more resource efficient concurrency

Task: Build a simple threadpool and then make your server use this threadpool to handle incoming connections and sending the response.

* Look at the documentation for channels in `std::sync::mpsc`
