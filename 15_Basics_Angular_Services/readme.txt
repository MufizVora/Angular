// Let's understand what are services in angular


What is Service?
    -> In Angular, a service is a way to share data and functionality across different components in your application. Services help keep your code organized and make it easier to maintain by promoting a separation of concerns.


Key Points:
    1. Reusable Code: Services can be reused across multiple components.
    2. Dependency Injection: Angular uses dependency injection to provide services to components, making it easy to manage dependencies.    


Example of a Simple Service
Let’s create a basic example of a service that fetches user data.

Step 1: Generate a Service
You can use the Angular CLI to generate a service:
Example: 
    command to create the service : ng generate service user
This creates a file named user.service.ts.

    
Step 2: Implement the Service
Open user.service.ts and add a method to return user data:
Example:
// user.service.ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class UserService {
  private users = ['Alice', 'Bob', 'Charlie'];

  getUsers() {
    return this.users;
  }
}
The @Injectable decorator marks the class as a service that can be injected into components.
The getUsers method returns a list of users.


Step 3: Use the Service in a Component
Now, let's use the UserService in a component:
Example:
// app.component.ts
import { Component } from '@angular/core';
import { UserService } from './user.service';

@Component({
  selector: 'app-root',
  template: `
    <h1>User List</h1>
    <ul>
      <li *ngFor="let user of users">{{ user }}</li>
    </ul>
  `,
})
export class AppComponent {
  users: string[];

  constructor(private userService: UserService) {
    this.users = this.userService.getUsers(); // Fetch users from the service
  }
}

Explanation:
1. Dependency Injection: The UserService is injected into the AppComponent through the constructor.
2. Using the Service: The component calls getUsers() to get the list of users and assigns it to the users property, which is then displayed in the template.