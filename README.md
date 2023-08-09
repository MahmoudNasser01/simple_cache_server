# Building a Simple Cache Server in Python

I'm a fan of small toy projects that have the sole purpose of demonstrating a concept. This is a small project that demonstrates how a cache server works.
I think it's important to balance toy projects with getting exposure to production-level code. While this project has been helpful for understanding the idea, an open source project like [Squid-Cache] (https://github.com/squid-cache/squid) is definitely on my reading list!
At the very simplest level, an HTTP server responds to requests. Let's take a look at a simple server that can respond to GET requests:
Here's a pseudo-code for a very basic HTTP server that can respond to GET requests:

```
- Wait for a request
  - When a request comes in, check what file it's looking for.
  - If we have it:
    - Great! Send it.
  - If we don't have it:
    - Send back a 404.
```

## Caching

At the very simplest level, a cache server is responsible for serving items that have already been requested from the main server. Doing this gives the main server a break from having to respond to every request, and the workload can be shared by the cache server.
Here's the pseudocode for a very basic cache server:

```
- Wait for a request
  - When a request comes in, check what file it's looking for.
  - If we have it stored in the cache:
    - Send it.
  - If we don't have it in the cache:
    - Request it from the main server
    - If the main server has it:
      - Store a copy in the cache
      - Send the file to the client
    - If the main server does not have it:
      - Send a 404 to the client
```

