While handling errors on the server side for your REST APIs:
* you MUST NEVER send stack traces to API clients
  * doing so provides too much insight into the inner workings of your application, potentially helping attackers
* you MUST NEVER send information about software and software versions as that could ease the work of an attacker
  * doing so provides too much insight into what is used to run your application. For example, if an attacker can find out that your application runs under Tomcat 8.5.1, then he can easily check all security flaws that your application server is not protected against and use these to attack your application and the underlying infrastructure
