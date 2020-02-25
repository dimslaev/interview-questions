### Hypertext Transfer Protocol

The communication protocol used for browsing the web. This protocol uses a **message based model** where your client makes an HTTP request to a web server and that server responds with a resource which is displayed in the browser.

#### The 4 main HTTP requests

- GET - read - used to request data from a specified resource where data is not modified it in any way as GET requests do not change the state of resource.

- POST - create - used to send data to a server to create a resource.

- PUT - update - used to update existing resource on a server by using the content in body of the request.

- DELETE - delete - The DELETE method deletes the specified resource.

#### HTTP Responses

1xx — Informational.
2xx — Successful responses.
3xx — Redirects.
4xx — Client errors.
5xx — Server errors.

- 200 OK - The request has succeeded.
- 301 - Moved Permanently
- 302 - Changed temporarily
- 400 Bad Request - The server could not understand the request due to invalid syntax.
- 401 Unauthorized
- 403 Forbidden

### Representational State Transfer (REST)

Representational state transfer (REST) is a architecture style where request and responses contain representation of the current state of the systems resource.

“Normal” way:
_http://carapp.com/search?make=wv&model=beetle_

REST-style:
_http://carapp.com/get/vw/beetle_

