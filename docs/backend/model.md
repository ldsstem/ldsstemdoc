# Model

```
app
|-- Component.php
|-- Course.php
|-- Lesson.php
|-- ...
```

The model defines the object of the data from the database. All the table/ data from the database will be firstly migrated as the Model and then apply changes, display and more further action in the Controller. All the model should have a one to one relationship to the corresponding table in the table.

<details>
  <summary>Click to expand!</summary>

 <p>


``` php

<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Component extends Model
{
    //
    protected $table = 'component';
    protected $primaryKey = 'id';
    public $timestamps = true;


    protected static function boot() 
    {
      parent::boot();
 
      static::deleting(function($components) {
        //  foreach ($components->outcomes()->get() as $outcomes) {
        //     $outcomes->delete();
        //  }
         foreach ($components->patterns()->get() as $patterns) {
            $patterns->delete();
         }
         foreach ($components->tasks()->get() as $tasks) {
            $tasks->delete();
         }
      });
    }

    //get the retlated pattern id 
    public function patternid(){
        return $this->hasMany(
            'App\ComponentPatternRelation',
            'component_id'
        )->where('is_deleted', 0)->select(['pattern_id','component_id']);
    }

    //get the related pattern details
    public function patterns(){
        return $this->hasManyThrough(
            'App\LearningPattern',
            'App\ComponentPatternTaskRelation',
            'component_id', 
            'id', 
            'id', 
            'pattern_id' 
        )->with(['tasks'])->orderBy('component_pattern_task_relation.sequence');
    }

    public function outcomeid(){
        return $this->hasMany(
            'App\ComponentOutcomeRelation',
            'component_id'
        )->where('is_deleted', 0)->orderBy('component_outcome_relational.sequence');
    } 

    public function outcomes(){
        return $this->hasManyThrough(
            'App\LearningOutcome',
            'App\ComponentOutcomeRelation',
            'component_id', //middle retioan table local id
            'id', // target table target id
            'id', // local table local id
            'outcome_id' //middle relation table target id
        )->with(['unit_outcomeid'])->orderBy('component_outcome_relational.sequence');
    }

    public function taskid(){
        return $this->hasMany(
            'App\ComponentTaskRelation',
            'component_id'
        )->where('is_deleted', 0)->select(['task_id','component_id']);
    } 

    public function tasks(){
        return $this->hasManyThrough(
            'App\LearningTask',
            'App\ComponentPatternTaskRelation',
            'component_id', //middle retioan table local id
            'id', // target table target id
            'id', // local table local id
            'task_id' //middle relation table target id
        )->with(["assessment", "assessmentid", "resourceid", "toolid", "componentid", "motivatorid", "feedbackid"])->orderBy('component_pattern_task_relation.sequence');
    }
    public function patterntaskid(){
        return $this->hasMany(
            'App\ComponentPatternTaskRelation',
            'component_id'
        )->where('is_deleted', 0)->select(['task_id','component_id', 'pattern_id', 'sequence'])->orderBy('sequence');
    } 


    public function courseid(){
        return $this->belongsTo('App\CourseComponentRelation', 'id', 'component_id');
    }

    public function sdlid(){
        return $this->hasMany(
            'App\ComponentSDLRelation',
            'component_id'
        )->where('is_deleted', 0);
    }

    public function dpid(){
        return $this->hasMany(
            'App\ComponentDPRelation',
            'component_id'
        )->where('is_deleted', 0);
    }

}


```
</p>
</details>

The above code is the example explaining how the model works. The ```protected $table = 'component'; ``` is the key command of a model which defines the model is connecting to which table in the database. The laravel model extension will directed transfer the properties from the database table to the model. Besides the basic defination of the model, it is needed to define the relation which means what is the relationship between this model and other models. The relationship can be one to one relationship, parent-childern relationship, one to many relationship, many to many relationship and etc. For example: 
``` php
  public function dpid(){
        return $this->hasMany(
            'App\ComponentDPRelation',
            'component_id'
        )->where('is_deleted', 0);
    }
```
describes the component has many dpid meaning the one to many relationship.

Please visit [Relationship](https://laravel.com/docs/6.x/eloquent-relationships) to find out more. 

Last but not least, you can also override the delete function like 
``` php
  protected static function boot() 
    {
      parent::boot();
 
      static::deleting(function($components) {

         foreach ($components->patterns()->get() as $patterns) {
            $patterns->delete();
         }
         foreach ($components->tasks()->get() as $tasks) {
            $tasks->delete();
         }
      });
    }
```

for special handling.