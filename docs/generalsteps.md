# General steps for new API setup from backend to frontend

{docsify-updated}

The following are just oversimplied instructions, please also studying the LDS source code carefully and refer to the detail documentation.

## 1. Modifying database

Create a migration file using the Laravel command:

```php artisan make:migration describe_the_change```

Edit this new file under ```/database/migrations```, mainly the ```up()``` and ```down()``` methods.

Run ```php artisan migrate``` to execute the migration.

## 2. Backend setup after adding a new DB table

### 2.1. Model

Create a new model (using [Eloquent ORM](https://laravel.com/docs/6.x/eloquent)), under ```/app```, which have a one-to-one relationship to the corresponding table.

```php artisan make:model ModelName```

Inside the file, this line defined how the model is connecting to a database table with the given name explicitly.

```protected $table = 'table_name';```

Besides the basic definition, we also need to define the [relationship](https://laravel.com/docs/6.x/eloquent-relationships) between this model and other models.

The relationship can be one-to-one relationship, parent-childern relationship, one-to-many relationship, many-to-many relationship and etc. This facilitate easy retrival and manipulation of associated models.

The ```self::deleting()``` function can also be overrided for special handling under ```boot()``` if just deleting a record from the table is not enough.

### 2.2. Controller

Create a new API controller by:

```php artisan make:Controller API TestController --api```

A new controller file will be generated at ```/app/Http/Controllers/API``` with default template.

Please fill in the corresponding logic (map to HTTP requests) as index(LIST), store(POST), show(GET), update(PUT) and destroy(DELETE).

For other special request, e.g. not just directly add/update/delete the default data object, you may add extra functions which can be called by special route later.

### 2.3. Route

Open ```routes/api.php``` and add this line to create the route (created ```/api/test``` in this case):

```Route::resource('test', 'API\TestController');```

Put it inside ```Route::middleware(['auth:api'])->group(function () {})``` to make it only available to logged in user.

Further permission handling also handled by two other middleware ```admin_auth``` and ```design_permission```, both can be found under ```/app/Http/Middleware```.

> For web display related APIs and their routes, refer to ```routes/web.php```

## 3. Frontend API definition

Finally all APIs should be defined at ```/resources/js/api.js```. It just simply use ```axios``` as HTTP client to send different requests to the endpoints, with a unique name given to each single request. For example:

```js
const courseRequest = axios.create({
    baseURL:  config.get('url')+'/api/course',
    headers: {
        "Content-type": "application/json; charset=UTF-8",
        "Authorization": 'Bearer ' +$('meta[name="apitoken"]').attr('content')
    },
  });
  export const apiCourseList = () => courseRequest.get(`/`);
  export const apiCourseGet = data => courseRequest.get(`/${data}`);
  export const apiCourseDelete = data => courseRequest.delete(`/${data}`);
  export const apiCourseCreate = data => courseRequest.post('/', JSON.stringify(data));
  export const apiCourseUpdate = data => courseRequest.put(`/${data.course_id}`, JSON.stringify(data));
  export const apiCourseShowAll =  data => courseRequest.get(`/showAll`);
  export const apiCourseShowUsergroup =  data => courseRequest.get(`/showUsergroup/${data}`);
  export const apiCourseClearComponent = data => courseRequest.delete(`/clearCourseComponent/${data}`);
  export const apiCourseClearLesson = data => courseRequest.delete(`/clearCourseLesson/${data}`);
  export const apiCourseGetPermission = data => courseRequest.get(`/getPermission/${data}`);
  export const apiCourseUpdatePermission = data => courseRequest.post('/updatePermission', JSON.stringify(data));
```

Note that APIs with additional level of path, e.g. ```/api/course/showUsergroup/${data}``` are those special handling method defined in controller.

Then inside the React JSX file, these APIs can be imported like this:

```import { apiCourseList, apiCourseGet } from '../../../api.js'```

And typical be called like:

```js
await apiCourseUpdate({

}).then(response => {

}).catch();
```
