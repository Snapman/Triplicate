# Triplicate
Database schema, functions, and stoed procedures that allow relational databases to act as triplestores.  In this case, this project allows PostgreSQL to act as a triplestore.

It's a crazy notion, I know.  Using a relational database as a triple store.  Why do that when you can use OrientDB or Neo4J?  Well, not everyone is fortunate enough to have an employer that will install any database technology you want to try.  Most are entrenched in relational databases because they are proven, reliable forms of data storage technology with tons of support.  Relational databases give lots of IT managers warm fuzzies.  The problem lies in trying to get these guys to try something new.

Triplicate uses a special database schema, functions, and stored procedures to make a relational database act like a triplestore.  How is that done?  A bit of explanation is in order (and some gross over-simplification).

Your typical relational database deals with specific data types, their associations, and the relations to other sets of data.  In order to create a relational database, you must know all the different types of data you will be using, their relationships to each other, and (ideally) the types and lengths of each data element (such as integer, string, text, BLOB< etc).  A triplestore doesn't care about these things.  All a triplestore does is connect what are essentially Strings to a relational database to other Strings in a *semantic* fashion.  *Semantic* in this case means in an English grammar-like fashion:

> [subject] --> [predicate] --> [object]

If you think about data in this fashion, the *predicate* becomes the most relatable concept, in that it relates the *subject* to the *object*.  But the relation in this case is just another string, not a foreign key relationship.  A triplestore can use these relationships to "reason" around the data, which helps the concepts of the Semantic Web and machines that can analyze data in a more intuitive fashion.  But it makes the job of modeling data that is already modeled in this fashion in a relational database.

So while triplestores are more top-of-the-waves data stores and relational databases are more bottom-of-the-waves data stores, how do you make relational databases act like triplestores?  Where they don't care what kind of data is put in or how the data is related?  You do what [add link here] did: you create one barebones database schema with tables for:

- Database data types (including NULL and *object*, which is an abstract triplestore concept)
- Subjects
- Objects
- Predicates
- Triples

Now, the relational database does what it is good at: store specific types of data in its database so that they can be quickly and efficiently stored, queried, and retrieved.  And you do another important thing: you shift the enforcement of the database's structure to the application.  You will still have to do the work of enforcing the database's schema and strucuture; you just won't do it in the database anymore.  Now, it is in the code.

This can be both a curse and a blessing.  On the one hand, you have a triplestore that is so universal that any application can use it.  And it is backed by mature, robust technology that has been relied upon for three decades.  On the other hand, all those relationships you would normally have the database enforce will now be in the application code.  It's up to you to decide whether the hassle is worth it, buy hey, at least you can commit the database's structure to a version control repository now!

Files are forthcoming.
