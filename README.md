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

**What's to come :**
  - *Add the with clause (set the relationships that should be eager loaded).*
    
[1]:https://laravel.com/docs/10.x/scout#where-clauses
