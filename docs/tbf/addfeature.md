# Add a feature to main design view

### Scenario

Add a new feature to the main design view as part of the single page app like "Course Information" and "Lesson Plan".

<img src="./image/add_feature_design_view.png">

### Example: Lesson Plan

Let's start by tracing the code of existing menu item at ```resources/js/container/design.jsx```.

```jsx
<ListItem
  button
  selected={activeStage === 'lessonPlan'}
  onClick={(event) => setActiveStage('lessonPlan')}
  classes={{
    selected: classes.pageListItem
  }}
>
  <ListItemIcon>
    <AvTimerIcon {...getIconStyle(activeStage === 'lessonPlan')} />
  </ListItemIcon>

  <ListItemText
    primary="Lesson Plan"
    primaryTypographyProps={{
      variant: "subtitle2",
      style: { ...getTextStyle(activeStage === 'lessonPlan') }
    }} />
</ListItem>
```

The method called when ```onClick``` is ```setActiveStage()```. Another method ```getDesignStageContent()``` will eventually get called and set the content on the right.

```jsx
case 'lessonPlan':
  return (
    <Grid item xs>
      <LessonPlan />
      <Grid container item xs={12} justify={"flex-end"}>
        <Button variant={"outlined"} color={"primary"} onClick={() => setActivePage('componentPlan')}> Back </Button>
        <Button variant={"outlined"} color={"primary"} onClick={() => setActivePage('finish')}> Next </Button>
      </Grid>
    </Grid>
  );
```

In this case it display the ```<LessonPlan />``` component which is imported and defined at ```resource/js/design/lesson/container/lessonPlanContainer.jsx```. For this case nothing need to be passed into it.

Let's look at ```LessonPlanContainer``` which is the main container for lesson plan, it may further import other container and components, but it is not our focus here. The only important code is the few lines of ```import``` statements at the top of the file:

```jsx
import {ContextStore} from '../../../container/designContainer'
import {AppContextStore} from '../../../container/app';

import {
    apiCourseUpdate,
    apiLessonCreate, apiLessonDelete
} from '../../../api.js';
```

The ```ContextStore``` and ```AppContextStore``` contain all the global data store and functions which can be reused easily. The API methods are imported from the master ```api.js``` file, if you have wrapped the api yourself, you may import you own file instead.

For example to check permission, these few lines do the job:

```jsx
const { course, forceUpdateCourse } = React.useContext(ContextStore);
// ... code skipped
const enableAdd = course.permission > 2;
const enableDelete = course.permission > 2;
const enableDrag = course.permission > 2;
```

It just grap the ```permission``` variable from the global ```course``` object and check its value.

This should be all that it take to put an existing feature into the main LDS app.

>However you may still need to fix whatever UI, CSS or position problems. These problems may happen becasue your feature use absolute positions (as now it is NOT occupying the whole page, calculation may), have confliction on CSS styles with LDS or other casue that need further debugging.

### Bonus: Reuse the existing "Task Setting" component

Refer to ```resources/js/design/lesson/component/lessonPlanView.jsx```, below just show the important lines of code, you will need to setup the data store, prepare data to pass into the component and set other states for UI control.

```jsx
import LearningTaskEditView from '../../task/component/learningTaskEditView';

// ... code skipped

// inside the return JSX, use the component inside a Dialog
<Dialog open={openTaskEdit} onClose={() => setOpenTaskEdit(false)} aria-labelledby="form-dialog-title" maxWidth={"md"}>
    <DialogTitle id="form-dialog-title">Edit Learning Task</DialogTitle>
    <DialogContent>
        <DialogContentText>
            You may add new learning task for this component...
        </DialogContentText>
        <LearningTaskEditView
            taskID={taskData.id}
            taskData={taskData}
            syncTask={setTaskData}
            showAssessment={false}
            error={error}
            mode="lesson_edit" />
    </DialogContent>

    <DialogActions>
        <Button onClick={() => setOpenTaskEdit(false)} >
            Cancel
        </Button>
        <Button variant="contained" color="primary" onClick={() => onSaveTask()} >
            Save
        </Button>
    </DialogActions>
</Dialog>
```
