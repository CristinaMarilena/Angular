# Angular
Documentation about Angular and any code to sustain it

## @Injectable

[] https://blog.ninja-squad.com/2016/12/08/angular-injectable/

DI system in Angular: it takes advantage of metadata on our code, added through **annotations**, to get all the information it needs so it can resolve dependencies.

 The @Injectable() decorator marks it as a service that can be injected, but Angular can't actually inject it anywhere until you configure an Angular dependency injector with a provider of that service.
 
 
## How Angular renders the base application

First, Ag needs at least one module and one component. A component is about functionality and structure, while a module is about packaging and distribution. 

## App component

### @Component

It s an annotation used to decorate the component(any generated component) by adding details that are related to the component but not to the component's controller logic. 
Angular uses this annotation and uses it with the controller class to **CREATE THE COMPONENT AT RUNTIME**.

The annotation declares that the class is a component by accepting an object. 

      @Component(
            { // the onject the component annotation accepts
              selector: 'app-client-transactions',
              templateUrl: './client-transactions.component.html',
              styleUrls: ['./client-transactions.component.css']
            }
      )

That object has a SELECTOR property that declares the **html selector of the component**. This means that the component is used in the template by adding the html tag : <app-root> </app-root> for ex, or <app-client-transactions></app-client-transactions>. 

The TEMPLATEURL property declares a link to a template containing an **HTML TEMPLATE**. 

Likewise, the styleUrls property contains an array of links to any CSS files that should be loaded for this component. 

### @NgModule

Just like a component, a module is an object with an decorator. The object here is called AppModule, and NgModule is the decorator. The first block is to import any Angular dependencies that are common to most apps and the App component.

The NgModule decorator takes an object with a few different properties. The declarations property is to provide a list of any components and directives to make available to the entire application.

The imports property is an array of other modules upon which this module depends—in this case, the Browser module (a collection of required capabilities). If you ever include other modules, such as third-party modules or ones you’ve created, they also need to be listed here.

The next property is the providers property, which is empty by default. Any services that are created are to be listed here, and we’ll see how to do this shortly.

Lastly, the bootstrap property defines which components to bootstrap at runtime. Typically, this will be the same App component, and the CLI already set it up for us. The bootstrap property should match the component that you bootstrap in the next section.
We’ve written code that creates a configuration for Angular to look at and understand how to render. The last step to look at is the code that gets executed at launch, which is called bootstrapping.

          //imports angular dependencies needed and components 
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { ClientTransactionsComponent } from './client-transactions/client-transactions.component';

         //uses the @ngmodule annotation to define a module by passing an object 
         @NgModule({
           declarations: [  // the object has declarations for listing any component or directive used in the application
             AppComponent,
             ClientTransactionsComponent
           ],
           imports: [ // other imports used in the application
             BrowserModule,
             AppRoutingModule
           ],
           providers: [],
           bootstrap: [AppComponent] // the first component to use to boostrap the application
         })
         export class AppModule { } //exports an empty class

## Building services
       
Although services will often help manage data, they’re not restricted to any particular job. The intention of a service is to enable reuse of code. A service might be a set of common methods that need to be shared. You could have various “helper methods” that you don’t want to write over and over, such as utilities to parse data formats or authentication logic that needs to be run in multiple places.


