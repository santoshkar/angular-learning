# angular-learning

Angular Self Learning

npm -> Node Package Manager

First, install node.js


> sudo npm install -g @angular/cli
> ng new <app name>				e.g. ng new my-first-app, this will create a new application with the name my-first-app
> cd my-first-app
> ng serve


[(ngModel)] = “name” in html where name is a variable in the type script, it’s a 2 way finding
also can access as {{name}} in html

ngModel is part of FormsModule. So you need to import the module in app.module.ts as: 
import { FormsModule } from ‘@angular/forms’

@NgModule ({
	:
	:
	imports: [
		FormsModule
	]

})


Type Script
Super script of java script. It provides features as class, interface, strong types etc. Type script is compiled to java script by CLI before running in the browser. 

installing bootstrap
npm install -save bootstrap@3 to install version 3
Imp: it should be run only inside your project path

Once it’s run, the boostrap folder will be created under node-modules folder. This folder will have all necessary files including the .css file.
In order to use the style of bootstrap, you need to make an entry in .angular-cli.json as

"styles": [
  "styles.css",
  "../node_modules/bootstrap/dist/css/bootstrap.css"
],


Components
Every component refers to a particular function in the UI. E.g. Home component, User component etc. It’s a reusable component.
Each component has it’s own business logic (throw TS), style etc.

The app component is the default and root component. Any new component you are going to create should be created under the folder app.

Step - 1 (Create Angular Component)
create a folder as server under app folder. In app/server, create file server.component.ts with contents:

import { Component } from '@angular/core';

@Component({
  selector: 'app-server',
  templateUrl: './server.component.html’            ———> create server.component.html under app/server folder
})
export class ServerComponent {

}

Step - 2 (Register Angular Component)
Register for this component to be scanned by Angular. In the root module i.e. app.module.ts

import { ServerComponent } from './server/server.component';
@NgModule({
  declarations: [
    AppComponent,
    ServerComponent
  ],
  imports: [
    BrowserModule,
    FormsModule
  ],
  providers: [ServerComponent],
  bootstrap: [AppComponent],
})

Step-3 (Create HTML which is entered in server.component.ts)

Step-4 (Use the template in html)
In app.component.html, use
<app-server>This is loading……..</app-server>


*Creating component using CLI

ng generate component servers
or
ng -g -c servers

*By creating this, you can simple skip step 2 (registering component) and creating other dependent files manually


Difference: template and templateUrl in the .ts file
try:
templateUrl: './servers.component.html'
or
template: '<app-server></app-server> <app-server></app-server>',
similarly you can write inline styles too in the .ts file.

Using selector as an attribute

In ts…………..
Old:
@Component({
  selector: 'app-servers',
  templateUrl: './servers.component.html',
  styleUrls: ['./servers.component.css']
})

New:
@Component({
  selector: '[app-servers]',				————— Used as attribute
  templateUrl: './servers.component.html',
  styleUrls: ['./servers.component.css']
})

In html……….
Old:
<app-servers></app-servers>


New:
<div app-servers></div>

Using selector as a class

In ts…………..
Old:
@Component({
  selector: 'app-servers',
  templateUrl: './servers.component.html',
  styleUrls: ['./servers.component.css']
})

New:
@Component({
  selector: '.app-servers',		————— Used as Class
  templateUrl: './servers.component.html',
  styleUrls: ['./servers.component.css']
})

In html……….
Old:
<app-servers></app-servers>


New:
<div class='app-servers'></div>

	

Data Binding

You can use both method and variable as:

{{variable}} or {{getMyMethod()}}

ts
public name = ‘Santosh';

public getName() {
  return this.name;
}


html
name : {{name}}
<br>
getName() : {{getName()}}



Property Binding

<button disabled>hello</button> 
	here the button is statically disabled. But we want to do it dynamically.

So first step, this property should be bind with a .ts variable as [property] = <variable>

so in .ts, 
	isDisabled = false;
in html:
	<button [disabled]=‘isDisabled’>hello</button> 

another example:
	<p [innerText]=‘isDisabled’></p>






