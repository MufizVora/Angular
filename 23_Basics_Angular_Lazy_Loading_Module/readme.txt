// Let's see what is lazy loading feature module


What is Lazy Loading Module?
    -> Lazy loading in Angular is a design pattern that allows you to load feature modules only when they are needed, rather than loading all modules upfront when the application starts. This helps reduce the initial load time and improves the performance of your application by splitting it into smaller, manageable chunks.


How Lazy Loading Works

1. Feature Modules: You create separate modules for different features of your application.
2. Router Configuration: You configure the Angular router to load these feature modules on demand.    


Example of Lazy Loading

Let’s create a simple application with two feature modules: HomeModule and AdminModule. The AdminModule will be lazy-loaded when the user navigates to the /admin route.

Step 1: Create Feature Modules
1. Generate Modules: You can generate feature modules using Angular CLI:

ng generate module home --routing
ng generate module admin --routing

This creates two modules with their own routing files.

2. Home Module: Update home-routing.module.ts to define the routes.

import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './home.component';

const routes: Routes = [
  { path: '', component: HomeComponent }
];

@NgModule({
  imports: [RouterModule.forChild(routes)],
  exports: [RouterModule]
})
export class HomeRoutingModule {}


3. Admin Module: Update admin-routing.module.ts to define the routes.

import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { AdminComponent } from './admin.component';

const routes: Routes = [
  { path: '', component: AdminComponent }
];

@NgModule({
  imports: [RouterModule.forChild(routes)],
  exports: [RouterModule]
})
export class AdminRoutingModule {}

Step 2: Configure App Routing
Now, set up your main routing configuration in app-routing.module.ts to use lazy loading for the AdminModule.

import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';

const routes: Routes = [
  { path: '', loadChildren: () => import('./home/home.module').then(m => m.HomeModule) },
  { path: 'admin', loadChildren: () => import('./admin/admin.module').then(m => m.AdminModule) },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule {}

Step 3: Create Components
Home Component: Create a simple HomeComponent.

import { Component } from '@angular/core';

@Component({
  selector: 'app-home',
  template: `<h2>Home Page</h2><a routerLink="/admin">Go to Admin</a>`,
})
export class HomeComponent {}


Admin Component: Create a simple AdminComponent.


import { Component } from '@angular/core';

@Component({
  selector: 'app-admin',
  template: `<h2>Admin Page</h2><a routerLink="/">Go to Home</a>`,
})
export class AdminComponent {}


Step 4: Update App Module
Make sure your main AppModule imports AppRoutingModule.

import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule, AppRoutingModule],
  bootstrap: [AppComponent]
})
export class AppModule {}


Explanation of Lazy Loading

1. Feature Modules: HomeModule and AdminModule are created to encapsulate related functionality.
2. Lazy Loading with Router: The loadChildren property in the routing configuration tells Angular to load the specified module only when the user navigates to the corresponding route (/admin in this case).
3. Performance Improvement: When the application starts, only the HomeModule is loaded. The AdminModule is loaded only when the user clicks on the link to navigate to the admin page, reducing the initial bundle size and speeding up the load time.


Summary

1. Lazy Loading: A technique to load feature modules on demand rather than at the start of the application.
2. Improved Performance: By splitting the application into smaller chunks, you improve the loading speed and performance.
3. Easy Setup: Lazy loading is simple to configure using Angular’s router and module system.

Using lazy loading helps create efficient Angular applications that are faster and more responsive for users!