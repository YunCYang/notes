# Network

## Network Protocol

A network protocol describes a style of communication over a network. There are protocols for sending email, for fetching email, for sharing files.

### Hypertext Transfer Protocol (HTTP)

HTTP is a protocol for retrieving named resources (chunks of information, such as web pages or pictures). It specifies that the side making the request should start with a line like this, naming the resource and the version of the protocol that it is trying to use:

`GET /index.html HTTP/1.1`

HTTP treats the network as a streamlike device into which you can put bits and have them arrive at the correct destination in the correct order. TCP ensures this isn't a problem.

### Transmission Control Protocol (TCP)

All Internet-connected devices use TCP, and most communication on the Internet is built on top of it.

A TCP connection works as follows: one computer must be waiting, or listening, for other computers to start talking to it. To be able to listen for different kinds of communication at the same time on a single machine, each listener has a number (called a port) associated with it. Most protocols specify which port should be used by default.

Another computer can then establish a connection by connecting to the target machine using the correct port number. If the target machine can be reached and is listening on that port, the connection is successfully created. The listening computer is called the server, and the connecting computer is called the client.

### World Wide Web

The World Wide Web is a set of protocols and formats that allow us to visit web pages in a browser.

To become part of the Web, all you need to do is connect a machine to the Internet and have it listen on port 80 with the HTTP protocol so that other computers can ask it for documents.

Each document on the Web is named by a Uniform Resource Locator (URL), which looks something like this:

```
  http://eloquentjavascript.net/13_browser.html
 |      |                      |               |
 protocol       server               path
```

[Back](../../README.md)
