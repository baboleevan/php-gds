# Google Datastore Library for PHP #

[Google Cloud Datastore](https://cloud.google.com/datastore/) is a great NoSQL solution, but it can be tricky (i.e. there's lots of code glue needed) to get the "Hello World" of data persistence up and running in PHP.

This library is intended to make it easier for you to get started with and to use Datastore in your applications.

## Basic Examples ##

I find examples a great way to decide if I want to even try out a library, so here's a couple for you (without the boilerplate)...

```php
// Let's create a new Book object with some data
$obj_book = new Book();
$obj_book->title = 'Romeo and Juliet';
$obj_book->author = 'William Shakespeare';
$obj_book->isbn = '1840224339';

// And write it to Datastore
$obj_book_store->upsert($obj_book);
```

Now let's pull some data out of Datastore

```php
// Fetch all the books, using a GQL query, and show their titles and ISBN
$arr_books = $obj_book_store->query("SELECT * FROM Book");
foreach($arr_books as $obj_book) {
    echo "Title: {$obj_book->title}, ISBN: {$obj_book->isbn}", PHP_EOL;
}
```

## Getting Started ##

You'll need 
- a Google Account (doh)
- a Project to work on with the "Google Cloud Datastore API" turned ON [Google Developer Console](https://console.developers.google.com/)
- a "Service account" and a P12 key file for that service account [Service Accounts](https://developers.google.com/accounts/docs/OAuth2#serviceaccount)

## Running the examples ##

You will need to create 2 files in the `examples/config` folder as follows
- `config.php` (you can use `_config.php` as a template)
- `key.p12`

Or, you can pass in your own `Google_Client` object, configured with whatever auth you like.

## More About Google Cloud Datastore ##

"Use a managed, NoSQL, schemaless database for storing non-relational data. Cloud Datastore automatically scales as you need it and supports transactions as well as robust, SQL-like queries."

https://cloud.google.com/datastore/

### Specific Topics ###
Some highlighted topics you might want to read up on
- [Entities, Data Types etc.](https://cloud.google.com/datastore/docs/concepts/entities)
- [More information on GQL](https://cloud.google.com/datastore/docs/concepts/gql)
- [Indexes](https://cloud.google.com/datastore/docs/concepts/indexes)

## Footnotes ##

I am certainly more familiar with SQL and relational data models so I think that may end up coming across in the code - rightly so or not!

Not that it matters too much, I've been trying to decide what sort of Patterns this library contains. [PEAA](http://martinfowler.com/eaaCatalog/index.html).

What I decided is that I'm not really following DataMapper or Repository to the letter of how they were envisaged.

Probably it's closest to DataMapper. 
