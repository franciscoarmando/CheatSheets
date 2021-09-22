# Angular Cheat Sheet  # 

```
ng new ProjectName --minimalist=true

```

 ##Create component##

```
ng g component components/componentname 

@Component ({
  selector: "app-root",
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"]
```

## Create Models (manual) ##  

```
export class Todosm {
    Id: number;
    Title : string;
    Dudate : Date;
    Mstatus : boolean;
}

@component
import { Todom } from "../../models/todosmodel";

todos : Todom[];

```

## aspnet core web ap and angular 7 crud ##

### Add efcore nuget ###


### models ###
### Data Anotations ### 

```
ColumnTypeName = "nvarchar()"

ConnectionString Json  
appsettings.json  min:14
migration code first 17:00

tools >pkgmanagerconsole 
```

### Add-Migration ###

Add controller w/ef 17:00
  
Change conff ?? min 27:


New Angular 28:00
ng serve-o
add bootstrap  on indexhtml 
font aweome

structure txt 32:00

crate components
ng cl 38

copy model from wen api model to angular model
 
div class row 
	div class colmd5
	div class colmd5

service 
register service 

ngform html mn:44
input 46 
add forms @app module 
form 53 
reset form 1:05
onSubmit form 
get data from form to service .1:07


httpClient obj 
import module 
send data form value component to service 1:10 
cors 1:13 

ngx toastr 1:18 
get 1:23

metodo en service 
this http.get().toPromise
add ervoce to componetts 
html table 1:26
