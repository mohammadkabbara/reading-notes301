# Who is Roy Fielding?

He helped write the first web servers, that sent documents across the internet… and then he did a ton of research explaining why the web works the way it does. His name is on the specification for the protocol that is used to get pages from servers to your browser.

## Why don’t the techniques that we use today work well when we need to be able to talk to all of the machines in the world?

Because web pages are designed to be understood by people. A machine doesn't care about layout and styling. Machines basically just need the data. Ideally, every URL would have a human readable and a machine readable representation. When a machine GETs a resource, it will ask for the machine-readable one. When a browser GETs a resource for a human, it will ask for the human-readable "representation" of that data.

## What is the HTTP protocol that Fielding and his friends created?

it is capable of describing the location of something anywhere in the world from anywhere in the world. It's the foundation of the web. You can think of it like GPS coordinates for knowledge and information.

## What does a GET do?

GET is used to request data from a specified resource.

## What does a POST do?

POST is used to send data to a server to create/update a resource.

## What does PUT do?

PUT is used to send data to a server to create/update a resource.

## What does PATCH do?

The HTTP PATCH request method applies partial modifications to a resource.
