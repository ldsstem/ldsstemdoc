# Route

```
app
|-- route
|       |
|       |-web.php
|       |-api.php
|-- ...
```

There are two main files in the route folder. The ```web.php``` is mainly use to handle the web display while the ```api.php``` is handling all the API requests via the middleware apiguard with the Laravel Passport.

``` php

    Route::resource('evidence', 'API\EvidenceController');
    Route::post('evidence_pdf', 'API\EvidenceResourceController@fileupload');

```

The above example show what LDS usually used. The LDS always route the RESTful API endpoint with ```Route::resouce``` to the targeted controller. Besides, we use the ```Route::post/ Route::get/ Route::put/ Route::delete ``` to cover the special endpoint which is no regular RESTful API.

To discover more, please check [Routing](https://laravel.com/docs/6.x/routing).