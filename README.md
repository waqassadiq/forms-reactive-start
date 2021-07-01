# MyFirstApp

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 6.0.0.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).

## Fixing a Bug

In the next lecture, we'll add some code to access the controls of our form array:

*ngFor="let hobbyControl of signupForm.get('hobbies').controls; let i = index"

This code will fail as of the latest Angular version.

You can fix it easily though. Outsource the "get the controls" logic into a method of your component code (the .ts file):

    getControls() {
      return (<FormArray>this.signupForm.get('hobbies')).controls;
    }

In the template, you can then use:

*ngFor="let hobbyControl of getControls(); let i = index"

Alternatively, you can set up a getter and use an alternative type casting syntax:

    get controls() {
      return (this.signupForm.get('hobbies') as FormArray).controls;
    }

and then in the template:

*ngFor="let hobbyControl of controls; let i = index"

This adjustment is required due to the way TS works and Angular parses your templates (it doesn't understand TS there).
Fullscreen
Default view
Go to Previous lecture
207. Reactive: Grouping Controls
Go to Next lecture
209. Reactive: Arrays of Form Controls (FormArray)

