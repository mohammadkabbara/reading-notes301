# The Repositories
In order to expose these entities as resources, let's create two repository interfaces for each of them, by extending the CrudRepository interface:

```
public interface LibraryRepository extends CrudRepository<Library, Long> {}
public interface AddressRepository extends CrudRepository<Address, Long> {}
```

# Creating the Associations
After persisting both instances, we can establish the relationship by using one of the association resources.

This is done using the HTTP method PUT, which supports a media type of text/uri-list, and a body containing the URI of the resource to bind to the association.

Since the Library entity is the owner of the association, let's add an address to a library:
```
curl -i -X PUT -d "http://localhost:8080/addresses/1" 
  -H "Content-Type:text/uri-list" http://localhost:8080/libraries/1/libraryAddress
```
If successful, this returns status 204. To verify, let's check the library association resource of the address:
```
curl -i -X GET http://localhost:8080/addresses/1/library
```
This should return the Library JSON object with name “My Library”.

To remove an association, we can call the endpoint with DELETE method, making sure to use the association resource of the owner of the relationship:
```
curl -i -X DELETE http://localhost:8080/libraries/1/libraryAddress
```

#  One-to-Many Relationship
A one-to-many relationship is defined using the @OneToMany and @ManyToOne annotations and can have the optional @RestResource annotation to customize the association resource.

# Many-to-Many Relationship
A many-to-many relationship is defined using @ManyToMany annotation, to which we can add @RestResource.

##  The Data Model
To create an example of a many-to-many relationship, let's add a new model class Author that will have a many-to-many relationship with the Book entity:
```
@Entity
public class Author {

    @Id
    @GeneratedValue
    private long id;

    @Column(nullable = false)
    private String name;

    @ManyToMany(cascade = CascadeType.ALL)
    @JoinTable(name = "book_author", 
      joinColumns = @JoinColumn(name = "book_id", referencedColumnName = "id"), 
      inverseJoinColumns = @JoinColumn(name = "author_id", 
      referencedColumnName = "id"))
    private List<Book> books;

    //standard constructors, getters, setters
}
```

# Testing the Endpoints With TestRestTemplate
Let's create a test class that injects a TestRestTemplate instance and defines the constants we will use:
```
@RunWith(SpringRunner.class)
@SpringBootTest(classes = SpringDataRestApplication.class, 
  webEnvironment = WebEnvironment.DEFINED_PORT)
public class SpringDataRelationshipsTest {

    @Autowired
    private TestRestTemplate template;

    private static String BOOK_ENDPOINT = "http://localhost:8080/books/";
    private static String AUTHOR_ENDPOINT = "http://localhost:8080/authors/";
    private static String ADDRESS_ENDPOINT = "http://localhost:8080/addresses/";
    private static String LIBRARY_ENDPOINT = "http://localhost:8080/libraries/";

    private static String LIBRARY_NAME = "My Library";
    private static String AUTHOR_NAME = "George Orwell";
}
```

# Enable Spring in Tests with JUnit 5
JUnit 5 defines an extension interface through which classes can integrate with the JUnit test.

We can enable this extension by adding the @ExtendWith annotation to our test classes and specifying the extension class to load. To run the Spring test, we use SpringExtension.class.

We also need the @ContextConfiguration annotation to load the context configuration and bootstrap the context that our test will use.

# The WebApplicationContext Object

WebApplicationContext provides a web application configuration. It loads all the application beans and controllers into the context.

We'll now be able to wire the web application context right into the test:


```
@Autowired
private WebApplicationContext webApplicationContext;
```

# MockMvc Limitations

MockMvc provides an elegant and easy-to-use API to call web endpoints and to inspect and assert their response at the same time. Despite all its benefits, it has a few limitations.