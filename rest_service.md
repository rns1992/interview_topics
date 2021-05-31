## RESTful Services

### Q. What is POST request used for?
- The POST verb is most-often utilized to **create** new resources. On successful creation, return HTTP status 201, returning a Location header with a link to the newly-created resource with the 201 HTTP status.
- POST is neither safe nor idempotent. It is therefore recommended for non-idempotent resource requests. Making two identical POST requests will most-likely result in two resources containing the same information.
  
### Q. What is GET request used for?
- The HTTP GET method is used to **read** (or retrieve) a representation of a resource. In the “happy” (or non-error) path, GET returns a representation in XML or JSON and an HTTP response code of 200 (OK). In an error case, it most often returns a 404 (NOT FOUND) or 400 (BAD REQUEST).
- According to the design of the HTTP specification, GET (along with HEAD) requests are used only to read data and not change it. Therefore, when used this way, they are considered safe. 
- That is, they can be called without risk of data modification or corruption—calling it once has the same effect as calling it 10 times, or none at all. Additionally, GET (and HEAD) is idempotent, which means that making multiple identical requests ends up having the same result as a single request.
- Do not expose unsafe operations via GET—it should never modify any resources on the server.
  
### Q. What is PUT request used for?
- PUT is most-often utilized for **update** capabilities, PUT-ing to a known resource URI with the request body containing the newly-updated representation of the original resource.
- However, PUT can also be used to create a resource in the case where the resource ID is chosen by the client instead of by the server.  
- PUT is not a safe operation, in that it modifies (or creates) state on the server, but it is idempotent. In other words, if you create or update a resource using PUT and then make that same call again, the resource is still there and still has the same state as it did with the first call.  

### Q. What is PATCH request used for?  
- PATCH is used for **modify** capabilities. The PATCH request only needs to contain the changes to the resource, not the complete resource.
- PATCH is neither safe nor idempotent. However, a PATCH request can be issued in such a way as to be idempotent, which also helps prevent bad outcomes from collisions between two PATCH requests on the same resource in a similar time frame. 
- Collisions from multiple PATCH requests may be more dangerous than PUT collisions because some patch formats need to operate from a known base-point or else they will corrupt the resource. Clients using this kind of patch application should use a conditional request such that the request will fail if the resource has been updated since the client last accessed the resource.
- For example, the client can use a strong ETag in an If-Match header on the PATCH request.  

### Q. What is DELETE request used for?   
- It is used to **delete** a resource identified by a URI

### Q. Categorize Http Status Code?
- 1xx Informational
- 2xx Success
  - 200 OK
  - 201 Created
  - 204 No Content
- 3xx Redirection
  - 304 Not Modified
- 4xx Client Error
  - 400 Bad Request
  - 401 Unauthorized
  - 404 Not Found
  - 403 Forbidden
  - 409 Conflict
  - 405 Method Not Allowed
  - 408 Request Timeout
  - 429 Too Many Requests
- 5xx Server Error
  - 500 Internal Server Error
  - 502 Bad Gateway
  - 504 Gateway Timeout
  - 503 Service Unavailable
