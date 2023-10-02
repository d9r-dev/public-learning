## MVC, MVP and MVVM

[MVC, MVP and MVVVM Design Pattern](https://medium.com/@ankit.sinhal/mvc-mvp-and-mvvm-design-pattern-6e169567bbad)

![Schematics of the Design Patterns](https://miro.medium.com/v2/resize:fit:786/format:webp/0*1ZrS8t3HvPzRAuqg.png)
- ### MVC
  
  * Model 
    * data that is required to display in the view
    * represents classes that describe business logic (business model and data model) and business rules how the data can be changed
  * View 
    * represents UI components like HTML or XML
    * displays data that it receives from the controller
    * monitors the model for change in data via the Observer pattern and displays the updated model
  * Controller 
    * is processing incoming requests
    * it processes the user data through the model and passing back the updated view
- ### MVP
  
  * Model 
    * as in MVC
  * View
    * component that directly interacts with the user via XML, Activity, fragments etc. 
    * does not contain any logic 
  * Presenter
    * receives the input from the View
    * proceses the data with the help of the Model
    * passes the results back to the View
    * communicates with the View through an interface that is defined in the Presenter class
    * the view implements the interface
    * View is completely decoupled therefore unit testing is easier
- ### MVVM
  
  * View-Model
    * supports two-way data binding
    * allows for automatic propagation of changes to the view
    * exposes methods and properties that helps to maintain the state of the view and the model
    * View has reference to View-Model but View-Model has no information about View
    * many Views can be mapped to one View-Model