# Save data in a local database using Room

Apps that handle non-trivial amounts of structured data can benefit greatly from persisting that data locally. The most common use case is to cache relevant pieces of data so that when the device cannot access the network, the user can still browse that content while they are offline.

The Room persistence library provides an abstraction layer over SQLite to allow fluent database access while harnessing the full power of SQLite. In particular, Room provides the following benefits:

Compile-time verification of SQL queries.
Convenience annotations that minimize repetitive and error-prone boilerplate code.
Streamlined database migration paths.

## Primary components
There are three major components in Room:

The database class that holds the database and serves as the main access point for the underlying connection to your app's persisted data.
Data entities that represent tables in your app's database.
Data access objects (DAOs) that provide methods that your app can use to query, update, insert, and delete data in the database.
The database class provides your app with instances of the DAOs associated with that database. In turn, the app can use the DAOs to retrieve data from the database as instances of the associated data entity objects. The app can also use the defined data entities to update rows from the corresponding tables, or to create new rows for insertion

## Defining data using Room entities 
When you use the Room persistence library to store your app's data, you define entities to represent the objects that you want to store. Each entity corresponds to a table in the associated Room database, and each instance of an entity represents a row of data in the corresponding table.

That means you can use Room entities to define your database schema without writing any SQL code.

## Two possible approaches
In Room, there are two ways to define and query a relationship between entities: you can model the relationship using either an intermediate data class with embedded objects, or a relational query method with a multimap return type.

Intermediate data class
In the intermediate data class approach, you define a data class that models the relationship between your Room entities. This data class holds the pairings between instances of one entity and instances of another entity as embedded objects. Your query methods can then return instances of this data class for use in your app.

For example, you can define a UserBook data class to represent library users with specific books checked out, and define a query method to retrieve a list of UserBook instances from the database:


```
@Dao
public interface UserBookDao {
   @Query("SELECT user.name AS userName, book.name AS bookName " +
          "FROM user, book " +
          "WHERE user.id = book.user_id")
   public LiveData<List<UserBook>> loadUserAndBookNames();
}

public class UserBook {
    public String userName;
    public String bookName;
}
```

## Accessing data using Room DAOs 
When you use the Room persistence library to store your app's data, you interact with the stored data by defining data access objects, or DAOs. Each DAO includes methods that offer abstract access to your app's database. At compile time, Room automatically generates implementations of the DAOs that you define.

By using DAOs to access your app's database instead of query builders or direct queries, you can preserve separation of concerns, a critical architectural principle. DAOs also make it easier for you to mock database access when you test your app.

## Anatomy of a DAO
You can define each DAO as either an interface or an abstract class. For basic use cases, you should usually use an interface. In either case, you must always annotate your DAOs with @Dao. DAOs don't have properties, but they do define one or more methods for interacting with the data in your app's database.

The following code is an example of a simple DAO that defines methods for inserting, deleting, and selecting User objects in a Room database:

```
@Dao
public interface UserDao {
    @Insert
    void insertAll(User... users);

    @Delete
    void delete(User user);

    @Query("SELECT * FROM user")
    List<User> getAll();
}
```
There are two types of DAO methods that define database interactions:

- Convenience methods that let you insert, update, and delete rows in your database without writing any SQL code.

- Query methods that let you write your own SQL query to interact with the database.

The following sections demonstrate how to use both types of DAO methods to define the database interactions that your app needs.
