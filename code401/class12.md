# @RequestMapping Consumes and Produces

Mapping media types produced by a controller method is worth special attention.

We can map a request based on its Accept header via the @RequestMapping headers attribute introduced above:
```
@RequestMapping(
  value = "/ex/foos", 
  method = GET, 
  headers = "Accept=application/json")
@ResponseBody
public String getFoosAsJsonFromBrowser() {
    return "Get some Foos with Header Old";
}
```

# @RequestMapping annotation now has the produces and consumes attributes, specifically for this purpose:
```
@RequestMapping(
  value = "/ex/foos", 
  method = RequestMethod.GET, 
  produces = "application/json"
)
@ResponseBody
public String getFoosAsJsonFromREST() {
    return "Get some Foos with Header New";
}
```

# Create Simple Queries

Spring Data JPA focuses on using JPA to store data in a relational database. Its most compelling feature is the ability to create repository implementations automatically, at runtime, from a repository interface.

To see how this works, create a repository interface that works with Customer entities as the following listing (in src/main/java/com/example/accessingdatajpa/CustomerRepository.java) shows:
```
package com.example.accessingdatajpa;

import java.util.List;

import org.springframework.data.repository.CrudRepository;

public interface CustomerRepository extends CrudRepository<Customer, Long> {

  List<Customer> findByLastName(String lastName);

  Customer findById(long id);
}
```

CustomerRepository extends the CrudRepository interface. The type of entity and ID that it works with, Customer and Long, are specified in the generic parameters on CrudRepository. By extending CrudRepository, CustomerRepository inherits several methods for working with Customer persistence, including methods for saving, deleting, and finding Customer entities.

Spring Data JPA also lets you define other query methods by declaring their method signature. For example, CustomerRepository includes the findByLastName() method.

In a typical Java application, you might expect to write a class that implements CustomerRepository. However, that is what makes Spring Data JPA so powerful: You need not write an implementation of the repository interface. Spring Data JPA creates an implementation when you run the application.

# Build an executable JAR

You can run the application from the command line with Gradle or Maven. You can also build a single executable JAR file that contains all the necessary dependencies, classes, and resources and run that. Building an executable jar makes it easy to ship, version, and deploy the service as an application throughout the development lifecycle, across different environments, and so forth.


**When we don't need the full functionality provided by JpaRepository and PagingAndSortingRepository, we can simply use the CrudRepository.**


Let's now have a look at a quick example to understand these APIs better.

We'll start with a simple Product entity:
```
@Entity
public class Product {

    @Id
    private long id;
    private String name;

    // getters and setters
}
```
And let's implement a simple operation – find a Product based on its name:

```
@Repository
public interface ProductRepository extends JpaRepository<Product, Long> {
    Product findByName(String productName);
}
```
That's all. The Spring Data Repository will auto-generate the implementation based on the name we provided it.

**Notice the typical CRUD functionality:**

save(…) – save an Iterable of entities. Here, we can pass multiple objects to save them in a batch

findOne(…) – get a single entity based on passed primary key value

findAll() – get an Iterable of all available entities in database

count() – return the count of total entities in a table

delete(…) – delete an entity based on the passed object

exists(…) – verify if an entity exists based on the passed primary key value

This interface looks quite generic and simple, but actually, it provides all basic query abstractions needed in an application.