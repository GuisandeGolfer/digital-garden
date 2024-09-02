---
{"dg-publish":true,"dg-path":"Projects/FastAPI Refresh for AI/HTTP Request + REST.md","permalink":"/projects/fast-api-refresh-for-ai/http-request-rest/"}
---


# HTTP Routes

`GET`
- should only retrieve data

`POST`
- submits an entity to the specified resource, often causing a change in state or side effects on the server.

`PUT`
- replaces all current representations of the target resource with the request payload.

`DELETE`
- should delete the specified resource. 

> [!book] A lot more verbs as well... 

## WebSockets vs REST 
---

![](https://www.youtube.com/watch?v=fG4dkrlaZAA&t=307s)

**Notes**

- Example - real time chatting application
- both architectures have at least a server  to manage messages and a DB for content
- John: REST sends POST request to /message api
- REST sends GET requests to /messages API as a poll continuously to see if there are any new messages for them
- I guess this is an outdated approach
- for efficiency: Web Sockets?
- ! Look into RabbitMQ for backend task management? 
- long polling = send poll and hold onto it until it gets a new message, before sending back a response


### What are inside HTTP REST Requests?
---