# Route

```
app
|-- route
|       |
|       |-web.php
|       |-api.php
|-- ...
```

There are two main files in the . The ```web.php``` is mainly to hanlde the web display while the ```api.php``` is handling all the api request via the middleware apiguard with the laravel passport.

``` php

    Route::resource('evidence', 'API\EvidenceController');
    Route::post('evidence_pdf', 'API\EvidenceResourceController@fileupload');

```

The above example show what LDS usually used. The LDS always route the RESTFul api endpoint with ```Route::resouce``` to the targeted controller. Besides, we use the ```Route::post/ Route::get/ Route::put/ Route::delete ``` to cover the special endpoint which is no regular RESTFul api.


To discover more, please check [Routing](https://laravel.com/docs/6.x/routing).