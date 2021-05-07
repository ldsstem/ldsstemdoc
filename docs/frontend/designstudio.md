# Design Studio

## Folder Strutcure
<details>
  <summary>Click to expand!</summary>

 <p>

```
resource/js
|-- design
|       |- component
|       |- dashboard
|       |   |- ...
|       |- evidence
|       |   |- ...
|       |- learningComponent
|       |   |- ...
|       |- lesson        
|       |   |- ...
|       |- outcome        
|       |   |- ...
|       |- pattern        
|       |   |- ...
|       |- printable        
|       |   |- ...
|       |- stem practice        
|       |   |- ...
|       |- task        
|       |   |- ...
|       |- timeline        
|       |   |- ...
|-- ...
```

</p>
</details>

The design studio contains all the data storage, such as course data, and the sub-modules, component that everythings which is useed in the design studio while creating, editing a learning design. The design.jsx will handle all the routing to the different sub-module according to incoming stage and modules. If you will to add a new module in this layer, please do it here. There are mainly two phases, setup stage(setting a brand new LD) and the design stage(main design flow for free editing the LD in design). Please check ```getStepContent```, ```getActiveStage``` and ```getDesignStageContent``` in the ```design.jsx``` for more details.

Followings are the sub-modules used in the Design Studio
* Dashboard: Dashboard module is for displaying stats and chart in order to analysis the LD in another view.
* Evidence: evidence module is for creating, editing and deleting the learning evidence
* Learning Component: Learning Component module is the biggest part of the design studio. Users can edit curriculumn component including the patterns, outcomes and tasks related to the parent CC here. It also contains different tasks, patterns containers for task editing and pattern editting. This module will be displayed while clickng the curriculum component.
* Lesson: This folder contains the containers and components used in the Lesson Plan. Users can add, edit and delete lesson here. Users can also add, sequence and remove the tasks to the related lesson.
* Outcome: This folder contains all the componets related to the LO.
* Pattern: This folder contains all the pattern components which is mainly used in the Curriculum Plan.
* Printable: This module is used to show the view only summary.
* Stem Practice: 
* Task: This folder contains all the tasks components which is mainly used in the Curriculum Plan, Lesson Plan and also Timeline.
* Timeline: 