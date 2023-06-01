# Week 4 Assessment

### Setup
* Fork this repository
* You may make edits directly in github
* For the Exercise section, you will want to be logged in to [replit](https://replit.com)

## Questions (8 points possible)
1. In your own words, how would you define an ORM?
ORM (object relational mapping) creates the connection between your database in pgAdmin and object oriented classes in Visual Studio. This allows us to create, manage, and manipulate the database using C# rather than SQL.
2. Given the two classes for bike and owner, update the classes to include a one-to-many relationship where each bike has one owner, and each owner can have many bikes.

    ```C#
    namespace BikeApp
    {
        public class Bike
        {
            public int Id { get; set; }
            public string Type { get; set; }
            public DateTime PurchaseDate { get; set; }
            public Owner Owner { get; set; }
        }
    }

    namespace BikeApp
    {
        public class Owner
        {
            public int Id { get; set; }
            public string Name { get; set; }
            public int Zipcode { get; set; }
            public List<Bike> Bikes { get; set; } = new List<Bike>();
        }
    }
    ```

3. When adding a new pizza table to our database, which of the following two commands would we run first? Why is it important to run these two line in that order?
    ```
    add-migration AddPizzaTable
    ```
    ```
    update-database
    ```
We would first need to run the "add-migration" cpomand before the "update-database" command. Add-migration needs to be run first because that commits (or saves) our code at this point. Update-database is what pushes our code in the form of a migration file to our database in pgAdmin, which contains the instructions of what SQL should be run on the database.

4. For all three parts of this question, imagine that you have used Entity Framework to create a database table using the following class and context. 
    * What will the table name be? Bikes
    * What will the column name(s) be? Id, Type, Date
    * What is the name of the database you are connecting to? Bike

    ```C#
    namespace BikeApp
    {
        public class Bike
        {
            public int Id { get; set; }
            public string Type { get; set; }
            public DateTime Date { get; set; }
        }
    }

    namespace BikeApp
    {
        public class BikeContext : DbContext
        {
            public DbSet<Bike> Bikes { get; set; }
            protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder) => optionsBuilder.UseNpgsql("Host=localhost;Username=postgres;Password=password123;Database=Bikes").UseSnakeCaseNamingConvention();
        }
    }
    ```

5. What type of data does the `Contains` LINQ method return?
    <br> a. String 
    <br> b. Integer 
    <br> c. Boolean <------ correct
    
## Exercise (5 points possible)

Fork the Replit below, and complete the 5 LINQ exercises.  Add a link to your forked repl here: [<YOUR LINK HERE>](https://replit.com/@SkylarSandler/Mod2Week4Assessment#main.cs)

(https://replit.com/@SkylarSandler/Mod2Week4Assessment#main.cs)

### Submission
* Submit a link to your forked repository in the Submission form provided in your slack channel.

## Rubric

This assessment has a total of 13 points possible.  A score of **9** or higher is a pass.

As a reminder, this assessment is for students and instructors to determine if there are any areas that need additional reinforcement!
