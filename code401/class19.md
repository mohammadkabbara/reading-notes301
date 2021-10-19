# Create a Message-handling Controller
In Spring’s approach to working with STOMP messaging, STOMP messages can be routed to @Controller classes. For example, the GreetingController (from src/main/java/com/example/messagingstompwebsocket/GreetingController.java) is mapped to handle messages to the /hello destination, as the following listing shows:
```
package com.example.messagingstompwebsocket;

import org.springframework.messaging.handler.annotation.MessageMapping;
import org.springframework.messaging.handler.annotation.SendTo;
import org.springframework.stereotype.Controller;
import org.springframework.web.util.HtmlUtils;

@Controller
public class GreetingController {


  @MessageMapping("/hello")
  @SendTo("/topic/greetings")
  public Greeting greeting(HelloMessage message) throws Exception {
    Thread.sleep(1000); // simulated delay
    return new Greeting("Hello, " + HtmlUtils.htmlEscape(message.getName()) + "!");
  }

}
```
This controller is concise and simple, but plenty is going on. We break it down step by step.

The @MessageMapping annotation ensures that, if a message is sent to the /hello destination, the greeting() method is called.

The payload of the message is bound to a HelloMessage object, which is passed into greeting().

Internally, the implementation of the method simulates a processing delay by causing the thread to sleep for one second. This is to demonstrate that, after the client sends a message, the server can take as long as it needs to asynchronously process the message. The client can continue with whatever work it needs to do without waiting for the response.

After the one-second delay, the greeting() method creates a Greeting object and returns it. The return value is broadcast to all subscribers of /topic/greetings, as specified in the @SendTo annotation. Note that the name from the input message is sanitized, since, in this case, it will be echoed back and re-rendered in the browser DOM on the client side.

# Make the Application Executable
Spring Boot creates an application class for you. In this case, it needs no further modification. You can use it to run this application. The following listing (from src/main/java/com/example/messagingstompwebsocket/MessagingStompWebsocketApplication.java) shows the application class:
```
package com.example.messagingstompwebsocket;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MessagingStompWebsocketApplication {

  public static void main(String[] args) {
    SpringApplication.run(MessagingStompWebsocketApplication.class, args);
  }
}
```
@SpringBootApplication is a convenience annotation that adds all of the following:

@Configuration: Tags the class as a source of bean definitions for the application context.

@EnableAutoConfiguration: Tells Spring Boot to start adding beans based on classpath settings, other beans, and various property settings. For example, if spring-webmvc is on the classpath, this annotation flags the application as a web application and activates key behaviors, such as setting up a DispatcherServlet.

@ComponentScan: Tells Spring to look for other components, configurations, and services in the com/example package, letting it find the controllers.

The main() method uses Spring Boot’s SpringApplication.run() method to launch an application. Did you notice that there was not a single line of XML? There is no web.xml file, either. This web application is 100% pure Java and you did not have to deal with configuring any plumbing or infrastructure.