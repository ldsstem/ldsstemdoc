# Controller

## Folder Strutcure

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
|   |-- Controllers.php
|   |-- RouteController.php
|
|-- ...
```

</p>
</details>

* RouteController.php: define all the web logic from the web routing endpoint, data passing to the view. For example, if we have a new web point, lets say ```http://localhost:8000/helloworld```. We need add the function to the ```RouteController.php``` after registering the web route in the ``` routes/web.php```.
