<p align="center"><img src="/art/logo.png" alt="Logo Seasoned Scout"></p>

## Introduction

Laravel Scout provides a simple, driver-based solution for adding full-text search to your Eloquent models. Once Scout is installed and configured, it will automatically sync your model changes to your search indexes. Currently, Scout supports:

- [Algolia](https://www.algolia.com/)
- [Meilisearch](https://github.com/meilisearch/meilisearch)

As can be seen in the scout documentation[1], when using the database driver, scout builder is extremely limited, as it only supports simple where clauses that work for basic numeric equality checks. This fork aims to solve that by adding the missing builder features one by one.

**Already added features :**
  - *Updated Where clause :*
    - An array of arrays can be passed as a parameter : where([['id', '>', 5],['id', '<', 10]]).
    - Any operator supported by the Eloquent Builder is now supported as well : '=', '<', '>', '<=', '>=', '!=', etc.
    - Clauses containing the operator like so : where('id', '>', 5).
    - All changes are fully backward compatible, If no operator is passed as a parameter, it will be assumed that the desired operator is '='
  - *Added With Clause (set the relationships that should be eager loaded):*
    - The with() method can now be called on search.
    - Example :
      - Define a relationship[2] inside your model : 
      - call it like so : User::search('alex')->with('podcasts')
      - you can specify which columns you want returned
        - if you want to return the url only for example, call it like this : with('podcasts:url')

**What's to come :**
  - *Make a composer package in order to make installation easier*
  - *Build rest of currently unsupported builder features*
    
[1]:https://laravel.com/docs/10.x/scout#where-clauses
[2]:https://laravel.com/docs/10.x/eloquent-relationships#clipText-46