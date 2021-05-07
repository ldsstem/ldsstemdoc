#Folder Structure

Following is the overall fold structure of the front end. All the front-end js files is located in the ```/resources/js```.

```
resource/js
|-- admin
|       |
|       |-dashboard
|       |   |- ...
|       |-sitemanagement
|       |   |- ...
|       |-template_builder
|       |   |- ...
|       |-usersmanagement
|       |   |- ...
|-- container
|       |- app.jsx
|       |- appContainer.jsx
|       |- design.jsx
|       |- designContainer.jsx
|       |- loginForm.jsx
|       |- registerForm.jsx
|       |- tourGuide.jsx
|-- components
|       |-... (all the reusable react component using in everywhere in the LDS)
|-- dashboard
|       |-component
|           |- ...
|       |-container
|           |- ...
|-- design
|       |- ...
|-- usergroup
        |- ...
```

There are some important files needed to be mentioned. The appContainer.jsx and app.jsx are the main container of the whole application once you . All the app modules will be display via the the app Container and generate the web application from the laravel back end web route and view display, and the data storage or built-in function would be stored at the app.jsx and served as the app container containing all the modules in the LDS.

If you have some built-in function to add and which is supposed can be used everywhere in the LDS, please build your function and put it in the content store of app.jsx. Also, if you want to build a new module, please also have a look on the app.jsx and register a new module in it. 
 
Secondly, the design.jsx and the designContainer.jsx are the container for the design studio. You may put the state, data and built-function in the design studio module if you want to use these globally inside the design studio.

Besides, there are two other files, loginForm.jsx and registerForm.jsx. They are served for building the view of login page, and the registeration page from the other entry of web route.


There are mainly four modules in LDS and they are Admin, Dashboard, Usergroup and Design Studio respectively. It will be talked in more details in the following section.

