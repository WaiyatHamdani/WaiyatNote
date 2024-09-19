## Table of Contents
- [Dependecies](#dependecies)
- [Step 1: Creating and Starting the Javalin Server](#creating-and-starting-the-javalin-server)
- [Step 2: Configuring Routes](#configuring-routes)
- [Step 3: Calling configureRoutes(app)](#calling-configureRoutes)
- [Note](#note)

## Dependecies
go to : mvnrepository.com
```xml
<!-- https://mvnrepository.com/artifact/io.javalin/javalin -->
<dependency>
    <groupId>io.javalin</groupId>
    <artifactId>javalin</artifactId>
    <version>6.1.6</version>
</dependency>
```

## Creating and Starting the Javalin Server
- Javalin.create(): This creates a new instance of Javalin. Think of it as setting up the basic web server.
- .start(7000): This tells Javalin to start the server on port 7000. 
```java
Javalin app = Javalin.create().start(7000);
``

## Configuring Routes
- the app parameter is the Javalin instance from step 1
- 
```java
private static void configureRoutes(Javalin app) {
    UserController userController = new UserController();
    CharacterController characterController = new CharacterController();

    // Define API routes (endpoints)
    app.post("/users/register", userController::registerUser);  // When a POST request is made to /users/register, call registerUser
    app.post("/users/login", userController::loginUser);        // Handle POST requests to /users/login
    app.get("/users/{id}", userController::getUserById);        // Handle GET requests to /users/{id}

    app.post("/characters", characterController::createCharacter);  // Create a character
    app.get("/characters/{id}", characterController::getCharacterById);  // Get character by ID
    app.put("/characters/{id}", characterController::updateCharacter);  // Update a character
    app.delete("/characters/{id}", characterController::deleteCharacter);  // Delete a character
}
```

## Calling configureRoutes
```java
configureRoutes(app); 
```

- when you see it when it all come together 
    - ```java
            public class JavalinUtil {

            public static void startServer() {
            // Step 1: Create the Javalin instance and start it
            Javalin app = Javalin.create().start(7000);  // Start the server on port 7000

            // Step 3: Call configureRoutes() 
            configureRoutes(app);  // Pass the 'app' instance to configureRoutes
            }

            // Step 2: Define routes and map them to the corresponding controller methods
            private static void configureRoutes(Javalin app) {
                // Create instances of controllers
                UserController userController = new UserController();
                CharacterController characterController = new CharacterController();

                // Define routes (endpoints)
                app.post("/users/register", userController::registerUser);  // POST request to /users/register
                app.post("/users/login", userController::loginUser);        // POST request to /users/login
                app.get("/users/{id}", userController::getUserById);        // GET request to /users/{id}
        
                app.post("/characters", characterController::createCharacter);  // POST request to /characters
                app.get("/characters/{id}", characterController::getCharacterById);  // GET request to /characters/{id}
                app.put("/characters/{id}", characterController::updateCharacter);  // PUT request to /characters/{id}
                app.delete("/characters/{id}", characterController::deleteCharacter);  // DELETE request to /characters/{id}
            }
        }
    ```

## Note
this " userController::registerUser " similar to :
- UserController userController = new UserController();
- userController.registerUser();