# Triplicate
Add-on for Sesame that allows relational databases to act as triplestores.

It's a crazy notion, I know.  Using a relational database as a triple store.  Why do that when you can
use OrientDB or Neo4J?  Well, not everyone is fortunate enough to have an employer that will install
any database technology you want to try.  Most are entrenched in relational databases because they are
proven, reliable forms of data storage technology with tons of support.  Relation databases give lots
of IT managers warm fuzzies.  The problem lies in trying to get these guys to try something new.

Triplicate uses a special database schema, custom Sesame code, and a ton of stored procedures to make
a relational database act like a triplestore.  How is that done?  Take a look at the DDL for the database!
