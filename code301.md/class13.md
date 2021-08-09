

100’s =they usually tell the client that the header part of the request has been received and the server will try to comply with a transmission demand of the client

200’s =hey tell the client that its request was accepted. In case of asynchronous processing of a request (202)

300’s =They tell the client that the resource they are requesting isn’t available at the expected location anymore

400’s =They are all about invalid requests a client sent to a server. There are several causes to this, timeouts, wrong URI, missing authentication

500’s =Often they indicate problems with overwhelmed servers or unreachable servers behind proxies, but sometimes they can be directly related to client requests that trigger error exceptions on the server.

# What is a status code 202?
If the update is done asynchronous, this code can be used. It should include an URL to access the updated resource or an URL to check if the update has been succeeded. It can also include an estimation of how long the update will take.
# What is a status code 308?
This tells the client to use another URL to access the resource and not use the current URL anymore. It’s helpful when we have multiple endpoints for one resource, but don’t want to implement reading from all of them.

# What code would you use if an update didn’t return data to a client?
204 No Content 

# What code would you use if a resource used to exist but no longer does?
406 Not Acceptable 
# What is the ‘Forbidden’ status code?
 The client has authorized or doesn’t need to authorize itself, but still has no permissions to access the resource.

 # Why do we need to pull our MongoDB database string out of our server and put it into our .env?

 # What is middleware?
Middleware is software that provides common services and capabilities to applications outside of what's offered by the operating system.

 # What is the difference beween PUT and PATCH?
 PUT requires the client to send an entire representation of a resource to update it.

 PATCH requires the client only send parts of the representation of the resource to update it.

# What does a 500 error status code mean?


The HyperText Transfer Protocol (HTTP) 500 Internal Server Error server error response code indicates that the server encountered an unexpected condition that prevented it from fulfilling the request. This error response is a generic "catch-all" response

# What does the /:id mean in a route?

Route parameters are named URL segments that are used to capture the values specified at their position in the URL. The captured values are populated in the req.params object, with the name of the route parameter specified in the path as their respective keys.

# What is the difference between a status 200 and a status 201

The 200 status code is by far the most common returned. It means, simply, that the request was received and understood and is being processed. A 201 status code indicates that a request was successful and as a result, a resource has been created (for example a new page)


