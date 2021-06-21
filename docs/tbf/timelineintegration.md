# Timeline Integration

### List of requirements
1. Display timeline in the same interface as the main app
    - Since it is not just go to another page in a new tab, no more getting course id from URL, but it can be retrieved by ```import {ContextStore} from '../../../container/designContainer'```, and get the current active course
    - Once user click on the Timeline on the left menu, it display on the right hand side, i.e. display the ```<TimelineContainer />```
    - All UI postions and CSS style should be normal, and the Timeline should display properly on the right space like all other features, e.g. won't wrap under the left menu, won't display something outside of the viewport
2. Check permission of user and display timeline accordingly (currently edit mode or view-only mode).
    - Actually the course object returned by ```GET /course/{id}``` already contain the ```permission``` parameter inside.
    - By importing the main container (```designContainer```), you can also reuse all the global state, date and built-in funtion. Simply by using React hook ```React.useContext()``` in a function, then you can access the ```course``` object with ```permission``` parameter inside.
    - For frontend JSX code, you can use the ```permission``` parameter to make condition so that those add/edit/delete icons are not shown.
    - For backend API, PUT/POST/DELETE request to ```\course```, ```\lesson```, ```\learningTask```, etc are protected already.
3. (Deeper integration) Reuse components like the task setting form in the dialog

> **Remark:** Since timeline is using Redux, its code is different from other features in LDS, you may need to adapt the above explanation differently since there are state and reducer to deal with.