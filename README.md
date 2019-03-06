# Task Planner API

### Part 1: Task Planner API V1
1. Create a new Spring Boot project using the Spring Initializr: 
 https://start.spring.io/ 
![](images/project-config.png)
2. Create the Java Objects (POJOs) to Map the models of the Task Planner PWA: *User* and *Task*
3. Create an interface to define the contract of the *UserService* class. This service will handle all users's functionality:
    ```java
   public interface UserService {
        List<User> getUsersList();
        
        User getUserById();
        
        User createUser();
        
        User updateUser();
        
        void removeUser();
    }
    ```
4. Create an interface to define the contract of the *TaskService* class. This service will handle all users's functionality:
    ```java
      public interface TaskService {
            List<Task> geTasksList();
            
            Task getTaskById(String id);
            
            List<Task> getTasksByUserId(String userId);
            
            Task assignedTaskToUser(String taskId, User user);
            
            void removeTask();
            
            Task updateTask(Task task);
        }
    ```
5. Implement both contracts (UserService and TaskService).  

6. Configure your project so you can inject the services implementations anywhere in your project. Use the annotations *@Service* *@Autowired*. Check the official documentation and the following example as guidance:
https://docs.spring.io/spring-boot/docs/current/reference/html/using-boot-spring-beans-and-dependency-injection.html

7. Implement the REST controllers *TaskController* and *UserController*:
https://spring.io/guides/gs/rest-service/

8. Inject the *UserService* and *TaskService* on the respective controllers and test your API.

### Part 2: Consume Task Planner API from React JS App

1. Implemented the method *componentDidMount()* on the React component that displays the Tasks list. Inside the method use the function fetch to retrieve the Task list from the API
    ```javascript
    class App extends Component {
    
        constructor(props) {
            super(props);
            this.state = {
                tasksList: [],
            };
        }

        componentDidMount() {
            fetch('REPLACE-API-URL')
                .then(response => response.json())
                .then(data => {
                    let tasksList = [];
                    data.items.forEach(function (task) {
                        tasksList.push({
                           //Implement this part
                        })
    
                    });
                    this.setState({tasksList: tasksList});
                });
        }

        render() {
            return (
                <div>
                    <TasksList tasksList={this.state.tasksList}/>
                </div>
            );
        }
    }

    export default App;
    ```

2. In order to test your application I recommend Firefox browser. You must install the following plugin to avoid CORS validation restriction:

 https://addons.mozilla.org/en-US/firefox/addon/cors-everywhere/
    
