# Angular
Documentation about Angular and any code to sustain it

## @Injectable

[] https://blog.ninja-squad.com/2016/12/08/angular-injectable/

DI system in Angular: it takes advantage of metadata on our code, added through **annotations**, to get all the information it needs so it can resolve dependencies.

 The @Injectable() decorator marks it as a service that can be injected, but Angular can't actually inject it anywhere until you configure an Angular dependency injector with a provider of that service.
