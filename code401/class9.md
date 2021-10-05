# The HTTP Request Lifecycle

**Step 1: Local Processing**

Depending on how in depth you want to get, much can happen during this step depending on the application making the request. I am going to proceed on the understanding this request is being made by a browser, as opposed to cURL, an API client like Postman, or some other app.

**Step 2: Resolve an IP**

Like the processing done locally, resolving an IP from a "DNS server"2 is a sequence that includes many steps, and includes failovers if the first request fails to return an address.

**Step 3: Establish a TCP Connection**

Now that the client has an IP address, it can send an HTTP5 request, right? Almost, but first, since the request is sent over TCP6, which is a transport layer protocol like UDP, the client must open a TCP connection.

**Step 4: Send an HTTP Request**

Wow, that was a bunch of steps! But now that the client has an IP address and a TCP connection, it can finally send an HTTP request! Except…..no I’m kidding, we can send a request for real this time!

**Step 5: Tearing Down and Cleaning Up**

- Once the response has been fully delivered, the client sends a FIN packet at the TCP level, to which the server responds with an ACK, and then generally sends a FIN of its own, which the client responds to with its own ACK signal. The client then waits for a brief timeout, during which it cannot accept new connections, to prevent delayed packets from previous connections arriving during subsequent activities on the port.

- At this point, your browser begins processing what it has received. If it is an image, data, or other media file that is being consumed by some application inside the browser, a variety of things can happen.

## HttpUrlConnection

The HttpUrlConnection class allows us to perform basic HTTP requests without the use of any additional libraries. All the classes that we need are part of the java.net package.

The disadvantages of using this method are that the code can be more cumbersome than other HTTP libraries and that it does not provide more advanced functionalities such as dedicated methods for adding headers or authentication.

## Creating a Request

We can create an HttpUrlConnection instance using the openConnection() method of the URL class. Note that this method only creates a connection object but doesn't establish the connection yet.

## Adding Request Parameters

If we want to add parameters to a request, we have to set the doOutput property to true, then write a String of the form param1=value¶m2=value to the OutputStream of the HttpUrlConnection instance:

```Map<String, String> parameters = new HashMap<>();
parameters.put("param1", "val");

con.setDoOutput(true);
DataOutputStream out = new DataOutputStream(con.getOutputStream());
out.writeBytes(ParameterStringBuilder.getParamsString(parameters));
out.flush();
out.close();
```

## Setting Request Headers

Adding headers to a request can be achieved by using the setRequestProperty() method

## Configuring Timeouts

HttpUrlConnection class allows setting the connect and read timeouts. These values define the interval of time to wait for the connection to the server to be established or data to be available for reading.

To set the timeout values, we can use the setConnectTimeout() and setReadTimeout() methods

## Handling Cookies

The java.net package contains classes that ease working with cookies such as CookieManager and HttpCookie.

## Handling Redirects

We can enable or disable automatically following redirects for a specific connection by using the setInstanceFollowRedirects() method with true or false paramete

## Reading the Response

Reading the response of the request can be done by parsing the InputStream of the HttpUrlConnection instance.

To execute the request, we can use the getResponseCode(), connect(), getInputStream() or getOutputStream() methods

## Reading the Response on Failed Requests

If the request fails, trying to read the InputStream of the HttpUrlConnection instance won't work. Instead, we can consume the stream provided by HttpUrlConnection.getErrorStream().

## Building the Full Response

It's not possible to get the full response representation using the HttpUrlConnection instance.


