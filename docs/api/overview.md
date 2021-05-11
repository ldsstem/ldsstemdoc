# API Overview

In this section, we will talk about the structure on the API service. Also, we will provide some API request, and its response as the example. 

First, the Laravel routes the API endpoint in ``` routes/api.php ``` and mostly the corresponding API controller ``` app/HTTP/Controller/API/* ``` will do the correspinding handling logic for incoming RESTful API request. For more details, you might go to [Resource Controller](https://laravel.com/docs/6.x/controllers#resource-controllers).


# How to build an API Controller

In the remaining part, I would teach you how to build a brand new RESTful API service from scratch. There are two key elements to build an API service and they are: **Controller** and **Routes**.

To start with, we need to build an API Controller by running:

```php artisan make:Controller API/TestController --api```

The laravel framework will generate the API Controller file like 
```
<?php

namespace App\Http\Controllers\API;

use App\Http\Controllers\Controller;
use Illuminate\Http\Request;
use Auth;

class TestController extends Controller
{
    /**
     * Display a listing of the resource.
     *
     * @return \Illuminate\Http\Response
     */
    public function index()
    {
        //
        return response()->json();
    }

    /**
     * Store a newly created resource in storage.
     *
     * @param  \Illuminate\Http\Request  $request
     * @return \Illuminate\Http\Response
     */
    public function store(Request $request)
    {
        //
        return response()->json();
    }

    /**
     * Display the specified resource.
     *
     * @param  int  $id
     * @return \Illuminate\Http\Response
     */
    public function show($id)
    {
        //
        return response()->json();
    }

    /**
     * Update the specified resource in storage.
     *
     * @param  \Illuminate\Http\Request  $request
     * @param  int  $id
     * @return \Illuminate\Http\Response
     */
    public function update(Request $request, $id)
    {
        //
        return response()->json();
    }

    /**
     * Remove the specified resource from storage.
     *
     * @param  int  $id
     * @return \Illuminate\Http\Response
     */
    public function destroy($id)
    {
        //
        return response()->json();
    }
}
```
Please fill in the corresponding logic as index(LIST), store(POST), show(GET), update(PUT) and destroy(DELETE).

And then you might open the ``` routes/api.php ``` and add ```Route::resource('test', 'API\TestController');``` in order to routes the endpoint to the controller you just created.

Below is a list of endpoints we created in this example.

verb | endpoint | action
--- | --- | ---
GET	| /test | index
GET	| /test/{id} | show
POST |  /test | store
PUT/PATCH | /test/{id}	| update
DELETE | /test/{id} | destroy

