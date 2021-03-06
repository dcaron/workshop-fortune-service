# Exercise 2

## Goal
 
* Replace the static Fortune text by a random Fortune text that will be loaded from a H2 database.
* Add a Cloud Foundry [`manifest.yml`](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html#-example-manifest) 
file so we don't have to type in all the   

## Steps

* Introduce H2 database
* Introduce a JPA Entity `Fortune` with a `text` and `id` 
* Introduce JpaRepository to return a random Fortune Cookie from the database

Hint to load a Random Fortune from the database:

```java
// This query is not efficient, but ok for such s small DB
@Query(value="select * from fortune order by rand() limit 1", nativeQuery = true)
Fortune findRandomFortune();
```

* At startup insert Fortune Cookie messages in the database
* Expose the random Fortune Cookie text using the REST API
* Build the project using Maven and run it locally first
* Call the REST endpoint from the browser or curl to load the random Fortune text
* Introduce a Cloud Foundry `manifest.yml` that contains the application `name`, enables a `random-route` and `path` to the jar file to deploy
* If the application is working fine push the updated version of your application to Cloud Foundry
* Call the REST endpoint of the deployed application from the browser or curl to load the random Fortune text