# WalkThrough

### Scenario
Add the two 

First, we need to create a migration file to make the database changes in next migration. We can create the file through the laravel commond.

``` php artisan make:migration add_column_preposttiem_lesson ```

And then, we may find the file ``` add_column_preposttiem_lesson ``` we just created at ``` database/migration ```. Open the file, and fill in the changes we want to modify in this migration(Recalling that up is for the migration update and down is for the migration rollback).

``` php

<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class AddColumnPreposttiemLesson extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        //
        Schema::table('lesson', function (Blueprint $table) {
            $table->Integer('pre_time')->default(0);
            $table->Integer('post_time')->default(0);
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        //
        Schema::table('lesson', function (Blueprint $table) {
            $table->dropColumn('pre_time');
            $table->dropColumn('post_time');
        });
    }
}

```

Run the laravel command  ``` php artisan migrate ``` To execute the migration.

And now, we will have a lesson table with two new extra column.

Furthermore, to apply this database changes on the api, open the ```app/HTTP/Controller/API/LessonAPIController.php```. Please add 
```
  public static function save(Lesson $lesson, Request $request){
        ...

        if($request->has('time')){
            $lesson->time = $request->time;
        }

        if($request->has('pre_time')){
            $lesson->pre_time = $request->pre_time;
        }


        if($request->has('post_time')){
            $lesson->post_time = $request->post_time;
        }

        $lesson->is_deleted = 0;
        $lesson->created_by = Auth::user()->id;
        $lesson->updated_by = Auth::user()->id;
        $lesson->save();
        
        ...
        return $lesson;
    }
```

To apply the save changes in the lesson.