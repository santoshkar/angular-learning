<h1>Angular Self Learning</h1>

`npm -> Node Package Manager`

`First, install node.js`


`> sudo npm install -g @angular/cli`

`> ng new <app name>	`			e.g. ng new my-first-app, this will create a new application with the name my-first-app

`> cd my-first-app`

`> ng serve`


**[(ngModel)]** **= "name"** in html where name is a variable in the type script, it’s a 2 way finding
also can access as {{name}} in html

ngModel is part of FormsModule. So you need to import the module in app.module.ts as: 
import { FormsModule } from ‘@angular/forms’

<pre>
@NgModule ({
	imports: [
		FormsModule
	]
})
</pre>

<h3>Type Script</h3>

Super script of java script. It provides features as class, interface, strong types etc. Type script is compiled to java script by CLI before running in the browser. 

<h3>installing bootstrap</h3>

npm install -save bootstrap@3 to install version 3
Imp: it should be run only inside your project path

Once it’s run, the boostrap folder will be created under node-modules folder. This folder will have all necessary files including the .css file.
In order to use the style of bootstrap, you need to make an entry in .angular-cli.json as

<pre>
"styles": [
  "styles.css",
  <b>"../node_modules/bootstrap/dist/css/bootstrap.css"</b>
],
</pre>


<h3>Components</h3>

Every component refers to a particular function in the UI. E.g. Home component, User component etc. It’s a reusable component.
Each component has it’s own business logic (throw TS), style etc.

The app component is the default and root component. Any new component you are going to create should be created under the folder app.

**Step - 1** (Create Angular Component)
create a folder as server under app folder. In app/server, create file server.component.ts with contents:

import { Component } from '@angular/core';

<pre>
@Component({
  selector: 'app-server',
  templateUrl: './server.component.html’            ———> create server.component.html under app/server folder
})
export class ServerComponent {

}
</pre>

**Step - 2** (Register Angular Component)
Register for this component to be scanned by Angular. In the root module i.e. app.module.ts

<pre>
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
</pre>

**Step-3** (Create HTML which is entered in server.component.ts)

**Step-4** (Use the template in html)
In app.component.html, use

`<app-server>This is loading……..</app-server>`


<h4>*Creating component using CLI</h4>

<pre>
ng generate component servers
or
ng -g -c servers
</pre>

*By creating this, you can simple skip step 2 (registering component) and creating other dependent files manually


**Difference: template and templateUrl in the .ts file**

<pre>
try:
templateUrl: './servers.component.html'
or
template: '&lt;app-server>&lt;/app-server> &lt;app-server>&lt;/app-server>',
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
&lt;app-servers>&lt;/app-servers>


New:
&lt;div app-servers>&lt;/div>

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
&lt;app-servers>&lt;/app-servers>

New:
&lt;div class='app-servers'> &lt;/div>

</pre>

<h3>Data Binding</h3>

You can use both method and variable as:

{{variable}} or {{getMyMethod()}}

<pre>
ts
public name = ‘Santosh';

public getName() {
  return this.name;
}


html
name : {{name}}
<br>
getName() : {{getName()}}
</pre>


<h3>Property Binding</h3>


`<button disabled>hello</button>` <br>
	here the button is statically disabled. But we want to do it dynamically.

So first step, this property should be bind with a .ts variable as [property] = &lt;variable>

<pre>
so in .ts, 
	isDisabled = false;
in html:
	&lt;button [disabled]='isDisabled'>hello&lt;/button> 

another example:
	&lt;p [innerText]='isDisabled'></p>
</pre>





