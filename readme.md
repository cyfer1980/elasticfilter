### Install

```composer require orangeshadow/elasitcfilter```

- 1 ```php artisan vendor:publish```

- 2 Fill all fields in files: ```config/elastic_filter.php``` and ```config/indexes/{catalog}.php```

{catalog} - or your different name, You must enter all datamapping in this file

'className' - class must implement OrangeShadow\ElasticFilter\Contracts\IElasticImport;

- 3 Add next code to AppServiceProvider:
```
    $this->app->bind('ElasticManager', function(){
        $config = new IndexConfig('indexes.catalog');
            return new ElasticManager($config);
    });
```
- 4 Run command for indexing your Data
php artisan elastic:filter-index {indexes.catalog}
