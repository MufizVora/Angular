// Let's see what is Protected Routes in Angular


What is Protected Routes?
    -> In Angular, a Protected Auth Guard is a way to control access to certain routes in your application. It ensures that only authenticated (or authorized) users can access specific pages, and if a user is not authenticated, they are redirected to another page, like a login page.



How it works:

1. Guard: It's a service that protects routes from being accessed by unauthorized users.
2. CanActivate: It's a method that runs when a user tries to access a route. It checks if the user is authorized, and if they are not, it redirects them to a login or some other page.    

Simple Example of a Protected Auth Guard
1. Create the Auth Guard:
First, generate an auth guard using Angular CLI:

Example :
ng generate guard auth

This creates an auth.guard.ts file. Inside this file, we'll define how we check for authentication.

2. Define the Auth Guard:
In the auth.guard.ts file, we implement the CanActivate method.


import {
  CanActivateFn,
  Router,
  ActivatedRouteSnapshot,
  RouterStateSnapshot,
} from '@angular/router';
import { inject } from '@angular/core';
import { session } from '../utils/session';

export const authGuard: CanActivateFn = (
  route: ActivatedRouteSnapshot,
  state: RouterStateSnapshot
) => {
  const router: Router = inject(Router);
  const protectedRoutes: string[] = ['/dashboard'];
  return protectedRoutes.includes(state.url) && !session
  ? router.navigate(['/'])
  : false;
};


3. Protect Routes Using the Guard:
Now, we need to protect specific routes by adding the AuthGuard to them in the routing module.

In app-routing.module.ts, you can add the guard to a route like this:

import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './components/home/home.component';
import { AboutComponent } from './components/about/about.component';
import { DashboardComponent } from './components/dashboard/dashboard.component';
import { authGuard } from './guards/auth-guard.guard';

const routes: Routes = [
  {path: '', title: 'Home', component: HomeComponent},
  {path: 'about', title: 'About', component: AboutComponent},
  {
    path: 'dashboard',
    title: 'Dashboard',
    component: DashboardComponent,
    canActivate: [authGuard],
  }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }


Key Concepts:
canActivate: This method checks if the user is allowed to visit a route.
AuthGuard: This is a service that contains the logic for protecting routes.
localStorage: In the example, we're checking if a user exists in localStorage to determine if the user is authenticated. In real applications, you might check for a valid authentication token.


Conclusion:
A protected auth guard helps control which parts of your Angular app are accessible to authenticated users and prevents unauthorized access by redirecting users who aren't logged in.