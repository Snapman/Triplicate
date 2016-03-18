# Triplicate
Triplicate is a database schema, a set of functions, and a set of stored procedures that allow relational databases to act as triplestores.  Currently this project allows PostgreSQL to act as a triplestore, but in the future, it should be able to allow other relational databases to act as triplestores.

It's a crazy notion, I know.  Using a relational database as a triplestore.  Why do that when you can use OrientDB or Neo4J?  Well, not everyone is fortunate enough to have an employer that will let you use any data storage technology you want.  Most IT shops are entrenched in relational databases (and their insane license and support contracts) because they are proven, reliable forms of data storage technology with tons of support.  Relational databases give IT administrators lots of warm fuzzies.  The problem lies in trying to get these guys who are swimming in warm fuzzies to try the cold for a bit.

Triplicate uses a special database schema, functions, and stored procedures to make a relational database act like a triplestore.  How is that done?  A bit of explanation is in order (and some gross over-simplification).

## Relational Databases vs. Triplestores

Your typical relational database deals with specific data types, their associations, and the relations to other sets of data.  In order to create a relational database, you must know all the different types of data you will be using, their relationships to each other, and (ideally) the types and lengths of each data element (such as integer, string, text, BLOB< etc).  A triplestore doesn't care about these things.  All a triplestore does is connect what are essentially Strings to a relational database to other Strings in a *semantic* fashion.  *Semantic* in this case means in an English grammar-like fashion:

> [subject] --> [predicate] --> [object]

If you think about data in this fashion, the *predicate* becomes the most relatable concept, in that it relates the *subject* to the *object*.  But the relation in this case is just another string, not a foreign key relationship.  A triplestore can use these relationships to "reason" around the data, which helps the concepts of the Semantic Web and machines that can analyze data in a more intuitive fashion.  But it makes the job of modeling data that is already modeled in this fashion in a relational database much harder.

To use an analogy, relational databases are like **cats**, and triplestores are like **dogs**.  **Cats** are typically more finicky, while **dogs** are more easy-going (relatively speaking).

##How to make a cat bark like a a dog

So how do we make a cat bark like a dog?  How do we create a data store which has a relational database as an underlying technology and make it ambivalent towards what is put into it?  You do [what Patrick van Bergen did](http://techblog.procurios.nl/k/news/view/34300/14863/semantic-web-marvels-in-a-relational-database-part-i-case-study.html "Semantic web marvels in a relational database - part I: Case Study"): you create a barebones database schema with tables for the following concepts:

- Database data types (including NULL and *object*, which is an abstract triplestore concept)
- Subjects
- Objects
- Predicates
- Triples

Then you create functions, stored procedures, and indexes that let you access these concepts quickly and efficiently.

Now, the relational database does what it is good at: store specific types of data in its database so that they can be quickly and efficiently stored, queried, and retrieved.  And another important thing happens: you shift the enforcement of the database's structure to the application.  You will still have to do the work of enforcing the database's schema and strucuture; you just won't do it in the database anymore.  Now, it is in the code.

This can be both a curse and a blessing.  On the one hand, you have a triplestore that is so universal that any application can use it.  And it is backed by mature, robust technology that has been relied upon for three decades.  On the other hand, all those relationships you would normally have the database enforce will now be in the application code.  It's up to you to decide whether the hassle is worth it.  I am aiming this project towards those who do not have a choice of underlying data storage technology and are most likely obligated to use a relational database such as Oracle or SQL Server.

Files are forthcoming.
