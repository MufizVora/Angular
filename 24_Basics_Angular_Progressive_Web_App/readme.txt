// Let's see what is progressive web app


What is Progressive-Web-App?
    -> Progressive Web Apps (PWA) are web applications that provide a native app-like experience on the web. They use modern web capabilities to deliver high performance, reliability, and engaging user experiences. PWAs can work offline, send push notifications, and be installed on a user's home screen, just like native apps.


Key Features of PWAs

1. Responsive: Works on any device (desktop, mobile, tablet).
2. Offline Capabilities: Can function without an internet connection using service workers.
3. App-like Experience: Feels like a native app with smooth interactions and navigation.
4. Installable: Users can add PWAs to their home screen for easy access.
5. Push Notifications: Can send updates to users even when the app is not open.    

Implementing PWA in Angular
Angular makes it easy to create a PWA using the Angular CLI. Here’s a simple guide to create a PWA with Angular.

Step 1: Create a New Angular Project
You can start by creating a new Angular project with the Angular CLI. If you don't have Angular CLI installed, you can install it using npm:

npm install -g @angular/cli

Then create a new Angular project:

ng new my-pwa

When prompted, you can choose to add routing and select a stylesheet format.

Step 2: Add PWA Support
Navigate to your project directory and add PWA support:

cd my-pwa
ng add @angular/pwa

This command modifies your project by adding a service worker and other PWA-related files, such as a manifest file.

Step 3: Review the Generated Files

1. ngsw-config.json: This is the configuration file for the Angular service worker.
2. manifest.webmanifest: This file defines how your app appears on the home screen, including the app name, icons, and theme color.
3. src/manifest.json: This file is created to configure your PWA’s appearance.
4. Service Worker: The Angular service worker is registered in your app, allowing offline capabilities.

Step 4: Modify manifest.webmanifest
You can customize the manifest.webmanifest to define the app's appearance. Here’s an example:

{
  "name": "My PWA",
  "short_name": "PWA",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#317EFB",
  "icons": [
    {
      "src": "assets/icons/icon-72x72.png",
      "sizes": "72x72",
      "type": "image/png"
    },
    {
      "src": "assets/icons/icon-96x96.png",
      "sizes": "96x96",
      "type": "image/png"
    },
    {
      "src": "assets/icons/icon-128x128.png",
      "sizes": "128x128",
      "type": "image/png"
    },
    {
      "src": "assets/icons/icon-144x144.png",
      "sizes": "144x144",
      "type": "image/png"
    },
    {
      "src": "assets/icons/icon-152x152.png",
      "sizes": "152x152",
      "type": "image/png"
    },
    {
      "src": "assets/icons/icon-192x192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "assets/icons/icon-384x384.png",
      "sizes": "384x384",
      "type": "image/png"
    },
    {
      "src": "assets/icons/icon-512x512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}

Step 5: Build and Serve Your PWA
To test your PWA, build your project for production:

ng build --prod

Then serve the built application using a local server. You can use http-server for this:

npm install -g http-server
http-server -p 8080 -c-1 dist/my-pwa

Now, navigate to http://localhost:8080 in your browser. You'll see your Angular PWA running!

Step 6: Testing PWA Features

1. Install the App: Open the app in a browser that supports PWAs (like Chrome). You should see an "Install" prompt.
2. Offline Capability: To test offline capabilities, open the browser’s dev tools, go to the Network tab, and set it to "Offline." Refresh the app to see if it still works.
3. Push Notifications: To implement push notifications, you would need to set up a push service and integrate it into your Angular app.

Summary
PWA: A Progressive Web App is a web application that behaves like a native app, offering features like offline access and push notifications.
Angular PWA: Using Angular CLI, you can easily set up a PWA with service workers and a manifest file.
Installation and Offline Functionality: PWAs can be installed on devices and can function offline, providing a seamless user experience.

PWAs are a powerful way to enhance your web applications, making them more accessible and user-friendly!