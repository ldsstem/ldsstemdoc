# Folder Strutcure

<details>
  <summary>Click to expand!</summary>

 <p>

```
ldsk12_beta
|-- app
|   |-- Controllers
|   |       |- API
|   |       |- Auth
|   |       |- ... Controllers
|   |-- Middleware
|   |-- ... Models 
|
|-- routes
|   |-- ...
|
|-- reousource
|   |-- views
```

</p>
</details>


* [Controller](backend/controller): define all the web/API controls, backend logic handling, and etc.
* [Model](backend/model): define all the models we use in the LDS System. 
* [Routes](backend/route): define all the web routing and API routing for the LDS System.
* [View](backend/view): simply a redirect point for receiving the web route from Laravel, passing the data as the React properties and generating the application via the React JS.