Let's understand the file structure of angular app

1 .angular
    -> The .angular folder is a hidden directory created by the Angular CLI to store Angular-specific settings and caches, primarily to speed up builds and keep track of Angular projects.

2 .vscode
    -> The .vscode folder is created by Visual Studio Code within your project directory to store workspace-specific settings and configurations. It customizes the editor's behavior and appearance for that particular workspace.

    1 - launch.json: Defines debugging configurations for your project. It specifies how VS Code should launch and debug your application.

    2 - tasks.json: Configures tasks that can be run from VS Code, such as build and test scripts.

    3 - extensions.json: Recommends extensions for your workspace. When someone opens the workspace, VS Code suggests installing these extensions.

3 node_modules
    -> The node_modules folder is where npm (Node Package Manager) installs all the packages required for your project. It's essentially a library of dependencies that your project relies on to function correctly.

4 .editorconfig
    -> .editorconfig is a configuration file that helps maintain consistent coding styles across different editors and IDEs. It works by defining coding style rules in a simple, standardized format.

5 .gitignore
    -> The .gitignore file is used to tell Git which files or directories to ignore in a project. This is useful for excluding files that are not supposed to be tracked, such as build artifacts, temporary files, and sensitive information.

6 angular.json
    -> The angular.json file is the workspace configuration file for Angular CLI projects. It provides the configuration settings for your project and its dependencies.

7 package.json
    -> The package.json file is a crucial part of any Node.js project, containing metadata about the project along with its dependencies, scripts, and other settings.

8 package-lock.json
    -> The package-lock.json file in a Node.js project is automatically generated when you run npm commands like npm install. It locks down the versions of installed dependencies, ensuring consistency across different environments.        

9 tsconfig.json
    ->The tsconfig.json file in a TypeScript project is used to configure the TypeScript compiler options for your project. It tells the TypeScript compiler how to compile your TypeScript code.    