## Introducing Databases
* What is a database?
   * A system for storing a collection of related information
* RDBMS is a relational storage concept for data
* Uses normalization
   * Typically 3 levels of normalization
   * If we store all of our data like an address for a person
      * Name
      * Street
      * City
      * State
      * Zip
    * No need to list State or City for all users in the address table
    * Normalization breaks out this data duplication into their own components, like a State or City tables
    * Then relate the State or City to the Address table
* Consists of services and applications for managing data
* Allows querying, updating, inserting and deleting of data
## Understanding Queries


## Database Connections
* Required for applications to access data
* Connections can be pooled
   * Collection of available database connections
   * Helps with performance and avoiding locking, etc
   * Can close idle connections
* Don't forget to open and close connections
   * Open connections are a security risk!
* Database connection string:
   * m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" & _ "Initial Catalog=Northwind;Integrated Security=True;"
   * SQLOLEDB = SQL Object Linking and Embedding Database
   * Source = SQL Server Instance Name
   * Initial Catalog = Which Database to connect to
   * Integrated Security = Authentication type, Windows auth, SQL, etc