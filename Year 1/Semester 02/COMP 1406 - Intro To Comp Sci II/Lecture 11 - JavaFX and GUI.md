(Chapter 5)

# MVC Paradigm in Java

Model-View-Controller (MVC) is an architectural pattern that separates an application into three main components, each with specific responsibilities. It's widely used in Java applications, particularly for GUI applications and web frameworks.


---
#### Core Components

**Model**
- Represents the application's data and business logic
- Independent of the user interface
- Notifies observers (typically views) when its state changes
- Responsible for data validation, processing, and persistence

```
public class UserModel {
    private String username;
    private String email;
    
    // Getters, setters, business logic methods
    public boolean validateEmail() {
        // Email validation logic
        return email != null && email.contains("@");
    }
    
    // Data persistence methods
    public void saveToDatabase() {
        // Database interaction code
    }
}
```


**View**
- Presents the model data to the user
- Renders the UI elements
- Sends user actions to the controller
- Can be implemented using Swing, JavaFX, JSP, or other UI technologies

```
public class UserView {
    public void displayUserDetails(String username, String email) {
        System.out.println("User: " + username);
        System.out.println("Email: " + email);
    }
    
    public String getUserInputFromUI() {
        // Code to get input from UI elements
        return "user input";
    }
}
```


**Controller**
- Acts as an intermediary between Model and View
- Processes user input from the View
- Updates the Model based on user actions
- Selects the appropriate View to display

```
public class UserController {
    private UserModel model;
    private UserView view;
    
    public UserController(UserModel model, UserView view) {
        this.model = model;
        this.view = view;
    }
    
    public void setUserName(String name) {
        model.setUsername(name);
    }
    
    public void setUserEmail(String email) {
        model.setEmail(email);
    }
    
    public void updateView() {
        view.displayUserDetails(model.getUsername(), model.getEmail());
    }
    
    public void processUserInput() {
        String input = view.getUserInputFromUI();
        // Process input and update model accordingly
    }
}
```


