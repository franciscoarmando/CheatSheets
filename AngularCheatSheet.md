# Angular Js #

-------------Project ---------------------------  

```  
ng new <name> [options]
--minimal=true|false

@Component({
  selector: "app-root",
  templateUrl: "./app.component.html",
  styleUrls: []
})

```
----------Bootstrapo --------------

```
$npm install bootstrap --save
style.css
import "~bootstrap/dist/css/bootstrap.css";
```

-----------models--------------------

```
ng g class shared/todo --type=model
/ src/app/shared/models/user.model.ts


import {Car} from "./car.model";
export class User {
  id: number;
  name: string;
  car: Car;
}
```

--------Component .-------------------
```
ng g c todo-details --spec=false --s
ng g s shared/todo --skipTest=true|false

@Component({
  selector: "app-root",
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"]
})
export class AppComponent {
  title = "AppTodo";
}
```

-----------Service----------------------------

```
ng g s services/srvtodo
ng g s shared/todo --skipTest=true

@app.module
-import { SrvtodoService } from "../../services/srvtodo.service";
-providers: [ SrvtodoService ],

@Component:
import { SvtodoService } from "../../services/svtodo.service";
constructor(private todoService: SrvtodoService) { }
ngOnInit() { this.svtodoservice.getTodos();}

@Service
getTodos(){};
this.todos= this.todoService.getTodos();
```

--------------HTTP CLIENT ------------------------------
``` 

app.module.ts: 
-import { HttpClientModule } from '@angular/common/http';
-imports:{
	HttpClientModule
}

// 2
@service: 
-import { HttpClient, HttpHeaders } from "@angular/common/http";
-import { Observable } from "rxjs";

constructor( private http : HttpClient ){}

getTodos(): Observable <Todo[]> {
	 Todourl :string = "https://";
	return this.http.get<Todo>(this.Todourl);


// 3
component:
@Injectable()
export class ConfigService {
  constructor(private http: HttpClient) { }
}

ngOnInit() {
	this.todoService.getTodos().subscribe(todos => {
	this.todo = todos;
	});
}

// Nota: Comming from Service 
deletePost(post){
	this.http.delete(this.url + '/' + post.id)
	.subscribe(response => {
		alert(response);
	})
}

deletePost(post){
	this.service.deleteTodos(post.id)
	.subscribe(response => {
		alert(response);
	},
	(error: Response ) => { 
		if(error.status === 404)
			alert(Not found);
		else
			alert(error);
	});
}

```

---------FORMS ---------------------------------

```
// Template Driven 
@app.module 
- import { FormsModule } from '@angular/forms';
-   imports: [
    BrowserModule,
    AppRoutingModule,
    FormsModule

<formls>
 <input [(ngModel)]="firstName" name="firstName" 
		#firtsName="ngModel" class="form-control" 
		(change)="LogName(firstName)">
  </input>
		
 @module TS 
  LogName(firstName) {
    console.log(firstName);
  }
  
 @service 
   constructor(private svtodoservice : SvtodoService ) { }
```

------TABLES  ---------------------------------

```
 <table class="table table-striped">
  <tr>
    <th>Id</th>
    <th>Title</th>
    <th>Duedate</th>
    <th>Satus</th>
  </tr>
  <tr *ngFor="let todo of todos | async ">
    <td>{{ todo.id | json }} </td>
    <td>{{ todo.title | json }} </td>
    <td>{{ todo.duedate | json }} </td>
    <td>{{ todo.mstatus | json }} </td>
  </tr>
</table>

```


----------Property Binding ------------------------ 

```
<td [textContent] = "Title">
 js export class Component {
	Title= "Las 2 vidas del diablo";
}
```
----------Att Binding ------------------------ 

```
<td [attr.colspan] = colSpan>
js
export class Component {
	colSpan=2;
}
```

-------------Class Binding-------------------

```
<button class="btn" [class.active]="isActive">ClickMe </button>
<button class="btn" [class.active]=" ? 'blue': 'white'">ClickMe </button
<button [style.background-color]="isActive ? '#fff' : '#000' " >ClickMe </button>

export class Component {
	isActive=false;
}

``` 

-------------Event Bubbling -----------------------

```
onSave($event)
{
	$event.stopPropagation();
 }

```
----------Key Code -----------------------------


```
<input (keyup) = "onKeyUp($event)" />
 onKeyUp($event){
	if($event.keydcode === 13 ) {
		// Do 
	}
 }
 
 <input #email (click)= "onClick(email.value)" />
 export class component{
  onClick(email){
	do(this.email);
 }
 }
```


---------Two Way Binding ------------------------

```
@app.module
import { FormsModule } from '@angular/forms';
imports[ FormsModule ]

<input [(ngModel)] = "email" (click)= "OnClick()">

OnClick()
{
	email= "a@b.c";
}
```

----Event Emitter  ---------------------------------

```

State -> Input  |  Output->Event
--Input 
<favorite [isenabel]= isEnable >
----
import [ Input]

class{
@input()isEnable: boolean
}

onClick(){
this.favorite= this.isEnable ; }

// Output 

<favorite [isenabel]= isEnable  (changeEmiter) = "OnChange()">

import { Output }
@Output()changeEmiter = new EventEmitter();

onChange(){
this.changeEmiter();
emit (this.isEnable;
emit ({ newObj: this.isEnable})
}
```