# 2.1 Task Planner API

### Part 1: Task Planner API V1
1. Create a new Spring Boot project using the Spring Initializr: 
 https://start.spring.io/
2. Create Plain Old Java Objects (POJOs) to map the models of the Task Planner PWA: *User* and *Task*
3. Create an interface to define the contract of the *UserService* class. This service will handle all users' functionality:
    ```java
   public interface UserService {
        List<User> getAll();
        
        User getById(String userId);
        
        User create(User user);
        
        User update(User user);
        
        void remove(String userId);
    }
    ```
4. Create an interface to define the contract of the *TaskService* class. This service will handle all tasks' functionality:
    ```java
      public interface TaskService {
            List<Task> geAll();
            
            Task getById(String id);
            
            List<Task> getByUserId(String userId);
            
            Task assignTaskToUser(String taskId, User user);
            
            void remove(String taskId);
            
            Task update(Task task);
        }
    ```
5. Implement both contracts: UserService and TaskService.  

6. Configure your project so that you can inject the services implementations anywhere in your project. Use the annotations *@Service* *@Autowired*. Check the official documentation and the following example as guidance:
https://docs.spring.io/spring-boot/docs/current/reference/html/using-boot-spring-beans-and-dependency-injection.html

7. Implement the REST controllers *TaskController* and *UserController* to expose the services:
https://spring.io/guides/gs/rest-service/

8. Inject the *UserService* and *TaskService* on the respective controllers and test your API.

### Part 2: Consume the Task Planner API from the React JS App

1. Implement the lifecycle method *componentDidMount()* on the React component that displays the Tasks list. Inside the method use the function fetch to retrieve the Task list from the API. For now, returning some sample data from the backend would be enough.
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

__TIP__ In order to test your application I recommend Firefox browser. You must install the following plugin to avoid CORS validation restriction:

 https://addons.mozilla.org/en-US/firefox/addon/cors-everywhere/
