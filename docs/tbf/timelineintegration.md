# Timeline Integration

### List of requirements

1. Display timeline in the same interface as the main app
    - Since it is not just go to another page in a new tab, no more getting course id from URL using ```window.location.href```, but the current active course object can be retrieved by ```import {ContextStore} from '../../../container/designContainer'```. You will also need to ```import React from 'react'``` and call the ```React.useContext()``` method; This way of accessing app data is widly use in most of the components so you can just study the code, e.g. ```resources/js/design/lesson/container/lessonPlanContainer.jsx```
      - For example, ```getCourseInfo()``` in ```resources/js/design/timeline/src/api.js``` will need to be changed, as you cannot always assume you can get the course ID in the URL
      - May consider follow other core LDS components by calling API endpoints and using ```ContextStore``` directly in the component JSX file
    - Once user click on the Timeline on the left menu, it display on the right hand side, i.e. display the ```<TimelineContainer />```. This is explained in another page [here](https://ldsstem.github.io/ldsstemdoc/#/tbf/addfeature).
    - All UI postions and CSS style should be normal, and the Timeline should display properly on the right space like all other features, e.g. won't wrap under the left menu, won't display something outside of the viewport
    - If there is any special feature that rely heavily on UI position, e.g. DIV cover certain area with absolute position, it may have problem (e.g. cover the left menu) after putting in the main interface
2. Check permission of user and display timeline accordingly (currently edit mode or view-only mode).
    - Actually the course object returned by ```GET /course/{id}``` already contain the ```permission``` parameter inside.
    - By importing the main container (```designContainer```), you can also reuse all the global state, date and built-in funtion. Simply by using React hook ```React.useContext()``` in a function, then you can access the ```course``` object with ```permission``` parameter inside.
    - For frontend JSX code, you can use the ```permission``` parameter to make condition so that those add/edit/delete icons are not shown.
    - For backend API, PUT/POST/DELETE request to ```\course```, ```\lesson```, ```\learningTask```, etc are protected already.
3. (Deeper integration) Reuse components like the task setting form in the dialog

> **Remark:** Since timeline is using Redux, its code is different from other features in LDS, you may need to adapt the above explanation differently since there are state and reducer to deal with.

### LDS nodejs_v14 branch
This branch ([nodejs_v14](https://github.com/ldsstem/ldsk12_beta/tree/nodejs_v14)) is created to make LDS frontend compatible with the latest Node.jd LTS version lts/fermium v14.17.1. If no problem is found from both team, it may be merged into the main branches.

All dependencie have been updated, and scripts are updated to use Laravel-Mix 6 standard format. There are still some problematic packages but there should be no error during code compile. All these 3 modes are tested and worked fine:

```bash
npm run dev
npm run watch
npm run prod
```

It is recommended to use [nvm](https://github.com/nvm-sh/nvm) to manage different version of node.js. Let say you need to recompile the JS code from an older version:

```bash
nvm use v14.17.1
npm install
npm run dev
```