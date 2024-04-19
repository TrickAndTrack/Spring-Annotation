# Spring-Annotation

` @Controller `annotation is typically used to annotate classes that handle user requests in a web application. When a request is received by the application, the Spring Framework uses the @Controller annotation to identify the controller that is responsible for processing the request.

`@RestController` which is used for RESTful web services. it's the combination of `@Controller` and `@ResponseBody` annotation.
it is a controller with @ResponseBody it is convert an object into JSON format. 

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

`@GetMapping`: which consumes the data: get. This annotation is used to map HTTP GET requests to a specific method in a controller. It is commonly used to retrieve data or perform read operations.

`@PostMapping`: produce: post-submit (submiting data).This annotation is used to map HTTP POST requests to a specific method in a controller. It is commonly used to create new resources or perform write operations.

`@DeleteMapping`: This annotation is used to map HTTP DELETE requests to a specific method in a controller. It is commonly used to delete resources.

`@PutMapping`: submit -->update This annotation is used to map HTTP PUT requests to a specific method in a controller. It is commonly used to update resources, replacing the entire resource.

`@PatchMapping` : This annotation is used to map HTTP PATCH requests to a specific method in a controller. It is commonly used to perform partial updates to resources, typically updating only specific fields.

`@RequestParam`
```
@Controller
public class UserController {

    @GetMapping("/users")
    public String getUsers(@RequestParam("page") int page, Model model) {
        // logic to retrieve users from database using page parameter
        model.addAttribute("users", users);
        return "user-list";
    }
}
```

the getUsers method is annotated with @RequestParam, which tells Spring to extract the value of the page request parameter from the incoming HTTP request, and bind it to the page method parameter.


`@Autowired` can also be used on constructor parameters and method parameters to indicate that Spring should automatically inject the required objects. This is known as constructor injection and method injection, respectively.

Note that the `@Autowired` annotation is part of Spring's dependency injection framework, and is not a standard Java annotation.

`@Value` is an annotation in Spring Framework that is used to inject values into fields or methods from external sources such as properties files or environment variables. This annotation can be used to inject values of any type, including strings, numbers, booleans, and arrays.

`@RequestParam`
Used to capture data from the query string of a URL.

The query string is the part that comes after the ? symbol and consists of key-value pairs separated by &.

Example: /users?name=John&age=30

Here, @RequestParam can be used to extract the values of name and age.

`@PathVariable`

Used to capture data from the path of a URL.

Path variables are defined as placeholders within the URL path enclosed in curly braces {}.

Example: /users/{id}
