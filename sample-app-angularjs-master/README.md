
The application is written in ES6 (transpiled using babel), and utilizes ES6 modules.
We are loading the modules and creating bundles using webpack 4.

There are many ways to structure a ui-router app.
We aren't super opinionated on application structure.
Use what works for you.
We organized ours in the following way:

- Sub-module (feature) organization
  - Each feature gets its own directory. 
  - Features contain states and components
  - Specific types of helper code (directives, services, etc) _used only within a feature_ may live in a subdirectory 
  named after its type (`/mymessages/directives`)
- Leveraging ES6 modules
  - Each state is defined in its own file
  - Each component (controller + template) is defined in its own file
  - Components exported themselves
  - Components are then imported into a states where they are composed into the state definition.
  - States export themselves
  - The `feature.module.js` imports all states for the feature and registers then with the `$stateProvider`
- A single angular module is defined for the entire application
  - Created, then exported from `bootstrap/ngmodule.js`
  - The ng module is imported into some other module whenever services, config blocks, directives, etc need 
  to be registered with angular.