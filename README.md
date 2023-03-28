# Spring-Annotation

` @Controller `annotation is typically used to annotate classes that handle user requests in a web application. When a request is received by the application, the Spring Framework uses the @Controller annotation to identify the controller that is responsible for processing the request.

`@RestController` which is used for RESTful web services. it's the combination of `@Controller` and `@ResponseBody` annotation.

`@RequestMapping` annotation is used to map a URL to either an entire class or a particular handler method. It has the following optional options.

`REST APIs ` uses multiple standards like HTTP, JSON, URL, and XML for data communication and transfer.

`@ResponseBody`

Alternatively, if we wanted to return a JSON object, we could specify the produces attribute in the @RequestMapping annotation, like this:
```
@Controller
public class MyController {
 
    @RequestMapping(value = "/person", produces = "application/json")
    @ResponseBody
    public Person getPerson() {
        Person person = new Person();
        person.setName("John Doe");
        person.setAge(30);
        return person;
    }
}
```
In this example, the getPerson() method returns a Person object, which will be serialized into the response body as JSON because the produces attribute is set to "application/json".

Overall, the @ResponseBody annotation is a powerful tool for building RESTful web services using Spring MVC, and it allows developers to easily serialize Java objects into a variety of formats for use in web-based APIs.


` @Required `annotation is a useful tool for ensuring that a bean's required properties are set before it is used, and can help catch configuration errors early in the development process.

```java
public class Person {

    private String name;
    
    @Required
    public void setName(String name) {
        this.name = name;
    }
    
    public String getName() {
        return name;
    }
}
```
In this example, the setName() method is marked with @Required, which means that Spring will throw an exception if this method is not called before the Person bean is used.

`@Configuration` annotation is a powerful tool for creating and configuring beans in the Spring application context, and is essential for creating complex and modular Spring applications.

`@ComponentScan:` Spring Boot application scans all the beans and package declarations when the application initializes. 

By default, Spring will scan the package containing the class annotated with `@SpringBootApplication` (or its predecessor `@EnableAutoConfiguration`) for Spring-managed beans. However, if you want to specify a different base package or packages, you can use the @ComponentScan annotation.


