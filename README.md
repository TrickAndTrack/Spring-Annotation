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
`@Configuration` By default, Spring will scan the package containing the class annotated with `@SpringBootApplication` (or its predecessor `@EnableAutoConfiguration`) for Spring-managed beans. However, if you want to specify a different base package or packages, you can use the @ComponentScan annotation.


`@ComponentScan:` Spring Boot application scans all the beans and package declarations when the application initializes. 

`@ModelAttribute` to bind request parameters to a method argument in a Spring MVC controller:
```
@Controller
public class UserController {

    @GetMapping("/users/{id}")
    public String getUser(@PathVariable Long id, @ModelAttribute User user) {
        // logic to retrieve user from database using id parameter
        return "user-details";
    }
}
```
 the getUser method is annotated with @ModelAttribute, which tells Spring to bind any request parameters with matching names to the User object passed as an argument. The id parameter is also annotated with @PathVariable, which tells Spring to bind the id parameter from the request URL to the id argument.

`@Component:` It is a class-level annotation. It is used to mark a Java class as a bean. 

`@Service`: It is also used at the class level. It tells the Spring that the class contains the business logic.	Same as `@component`

In this example, the UserService class is annotated with @Service, which tells Spring to treat it as a service component. The userRepository field is also annotated with @Autowired, which tells Spring to inject an instance of the UserRepository interface into the service.

`@Repository` : It is a class-level annotation. The repository is a DAOs (Data Access Object) that access the database directly. 

`@EnableAutoConfiguration` annotation tells Spring Boot to "guess" how you will want to configure Spring, based on the jar dependencies that you have added. For example, // 2) example: Spring Boot auto-configuration can automatically configure the Thymeleaf template resolver.

`@SpringBootApplication`: It is a combination of three annotations `@EnableAutoConfiguration`, `@ComponentScan`, and `@Configuration`.
