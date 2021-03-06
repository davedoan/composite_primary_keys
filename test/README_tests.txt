= Composite Primary Keys - Testing Readme

== Testing an adapter

There are tests available for the following adapters:

* ibmdb
* mysql
* oracle
* oracle_enhanced
* postgresql
* sqlite3

To run the tests for one of the adapters follow these steps (using mysql in the example):

* You will need the following gems:
    - rake
    - activerecord (3.1.0.rc5 or later)
    - mysql (or the adapter of your choice)

* Put your database connection settings in test/connections/databases.yml.
  Look at databases.example.yml for examples.

    mysql:
      adapter: mysql
      username: root
      database: composite_primary_keys_unittest

* rake -T mysql

    rake mysql:build_databases         # Build the MySQL test databases
    rake mysql:drop_databases          # Drop the MySQL test databases
    rake mysql:rebuild_databases       # Rebuild the MySQL test databases
    rake mysql:test                    # Run tests using the mysql adapter

* rake mysql:build_databases
* rake mysql:test

== Running tests individually

You can specify which test you'd like to run on the command line:

* rake mysql:test TEST=test/test_equal.rb

If you want to run closer to the metal you can cd into the test/
directory and run the tests like so:

* ADAPTER=mysql ruby test_equal.rb

== Logging

By default, ActiveRecord's log messages are sent to standard out when
running the tests. If you would prefer to send them to a file, specify
it as the environment variable CPK_LOGFILE:

* CPK_LOGFILE=cpk_test.log rake mysql:test
