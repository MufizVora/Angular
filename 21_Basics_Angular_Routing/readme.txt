// Let's see what is routing in angular


What is Routing?
    -> Routing in Angular refers to the mechanism that allows you to navigate between different views or components in your application. It helps create a single-page application (SPA) experience by enabling the loading of different components without refreshing the entire page.


Basic Routing Example
1. Setup Routing: First, you need to configure routing in your application. Import RouterModule in your app module and define your routes.    

import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { RouterModule, Routes } from '@angular/router';
import { AppComponent } from './app.component';
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent },
];

@NgModule({
  declarations: [AppComponent, HomeComponent, AboutComponent],
  imports: [BrowserModule, RouterModule.forRoot(routes)],
  bootstrap: [AppComponent],
})
export class AppModule {}


2. Create Components: Create the HomeComponent and AboutComponent.

Home Component (home.component.ts):

import { Component } from '@angular/core';

@Component({
  selector: 'app-home',
  template: `<h2>Home Page</h2><a routerLink="/about">Go to About</a>`,
})
export class HomeComponent {}

About Component (about.component.ts):

import { Component } from '@angular/core';

@Component({
  selector: 'app-about',
  template: `<h2>About Page</h2><a routerLink="/">Go to Home</a>`,
})
export class AboutComponent {}

3. Router Outlet: Add a <router-outlet> tag in your main template to indicate where the routed components should be displayed.

App Component Template (app.component.html):

<h1>My Angular App</h1>
<nav>
  <a routerLink="/">Home</a>
  <a routerLink="/about">About</a>
</nav>
<router-outlet></router-outlet>

Explanation of Basic Routing

1. Router Configuration: In the AppModule, we define routes that map URLs to components. The path property specifies the URL segment, and the component property specifies which component to display for that path.
2. Router Links: The routerLink directive is used to create links that navigate to different routes without reloading the page.
3. Router Outlet: The <router-outlet> is a placeholder where Angular will render the routed component based on the current URL.


What is Dynamic Routing?
    -> Dynamic routing allows you to pass parameters in the URL to load different data based on those parameters.

1. Modify Routes: Update the routes to include a parameter.

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent },
  { path: 'user/:id', component: UserComponent }, // Dynamic route
];

2. User Component: Create a UserComponent that reads the dynamic parameter.

import { Component, OnInit } from '@angular/core';
import { ActivatedRoute } from '@angular/router';

@Component({
  selector: 'app-user',
  template: `<h2>User ID: {{ userId }}</h2>`,
})
export class UserComponent implements OnInit {
  userId: string;

  constructor(private route: ActivatedRoute) {}

  ngOnInit() {
    this.userId = this.route.snapshot.paramMap.get('id'); // Get the dynamic parameter
  }
}

3. Link to User Component: Update the HomeComponent to link to a user.

<a [routerLink]="['/user', 1]">Go to User 1</a>
<a [routerLink]="['/user', 2]">Go to User 2</a>


Explanation of Dynamic Routing
1. Parameter in Route: The :id in the route path signifies a dynamic parameter. You can use any name for this parameter.
2. ActivatedRoute: In the UserComponent, we inject ActivatedRoute to access the route parameters using snapshot.paramMap.get('id').



What is Nested Routing?
    -> Nested routing allows you to define routes within other routes, creating a hierarchical structure.

1. Define Nested Routes: Update the routes to include child routes.

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent },
  { path: 'user/:id', component: UserComponent, children: [
      { path: 'details', component: UserDetailsComponent },
      { path: 'settings', component: UserSettingsComponent },
    ] 
  },
];

2. User Component Template: Update the UserComponent template to include a router outlet for the child components.


<h2>User ID: {{ userId }}</h2>
<nav>
  <a [routerLink]="['details']">User Details</a>
  <a [routerLink]="['settings']">User Settings</a>
</nav>
<router-outlet></router-outlet> <!-- For nested routes -->


3. Create Child Components: Create UserDetailsComponent and UserSettingsComponent.


import { Component } from '@angular/core';

@Component({
  selector: 'app-user-details',
  template: `<h3>User Details</h3>`,
})
export class UserDetailsComponent {}

@Component({
  selector: 'app-user-settings',
  template: `<h3>User Settings</h3>`,
})
export class UserSettingsComponent {}


Explanation of Nested Routing
1. Child Routes: In the UserComponent route, we define child routes for details and settings.
2. Nested Router Outlet: The <router-outlet> inside UserComponent allows Angular to display the child components when their routes are activated.


Summary

Routing: Enables navigation between different components in a single-page application.
Dynamic Routing: Allows parameters in routes for more flexible data loading.
Nested Routing: Organizes routes hierarchically, enabling the use of child components under a parent route.

Routing is a powerful feature in Angular that enhances user experience by enabling smooth navigation and interaction within your application!