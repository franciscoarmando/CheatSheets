# Laravel #

## Create new App ## 

```
composer create-project --prefer-dist laravel/laravel blog
php artisan serve


<a href="{{ route('posts.create')}}" class="btn">
laravel php artisan route:list

```

## Templates ## 

```
@ templates/layout.blade.php

<html>
<head>
<body>
	@yield('Content')
</body>
</html>

@welcome.blade.php
 directive*-    
@extends('layout')
@section('content')
<h1> Hello </h1>
@endsection 

@extends('layouts.app')


@extends('layouts.navigation')

@section('content')
<div class="container container-fluid">
<h2>Je suis create blade</h2>
</div>
@endsection

@yield('content') 

```

### css ###

```
 <link rel="stylesheet" href="<?php echo asset('css/app.css')?>" type="text/css"> 


 @if (Route::has('login'))
                <div class="top-right links">
                    @auth
                        <a href="{{ url('/home') }}">Home</a>
                    @else
                        <a href="{{ route('login') }}">Login</a>

                        @if (Route::has('register'))
                            <a href="{{ route('register') }}">Register</a>
                        @endif
                    @endauth
                </div>
            @endif
```

### DataBase ### 

```
@env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=homestead
DB_USERNAME=homestead
DB_PASSWORD=secret

migration 
php artisan make:migration create_mitable_table

-@App
php artisan tinker
php.ini 
[Pcre]
pcre.jit=@

```

### Models ### 

```
php artisan make:model myModel

class Todos extends Model
{
    //table name 
    protected $table = 'todos';
    protected $primaryKey = 'Id';
    public $timestamps = false;
    protected $dates = ['Created' , 'Duedate'];
    protected $fillable = ['Title'];
    protected $casts = ['mStatus' => 'boolean'];
}

```
  ### Mddleware ### 

```
php artisan make:middleware FirstMiddleware
```

 ###  Controller ### 

```
php artisan make:controller MyController
Route::resource('my','MyController');
php artisan make:controller PostController --resource 

@web.php
Route::get('/', function () {
    return view('welcome');
});

@web.php CLEA
resources/views/welcome.blade.php

Route::get(/, PagesController@index)
Route::get(/about, PagesController@about)

Route::resource('/myPage', 'PostController')

   */
    public funct
    {
        return view ('todos/index');
		 return view ('todos.index')->with('todos', $todos);
    }

```
### Views  ### 

```
@extends('layout.layout')
@extends('layout.navigation')

@section('content')

@endsection

  <tr>@foreach ($todos as $todo)
            <td>{{$todo->Id}}</td>
            <td>{{$todo->Title}}</td>
            <td>{{$todo->mStatus}}</td>
            <td>{{$todo->Duedate}}</td>

```

### Forms ### 

```
<form action="crea" method="post">
$title = $request->input('Title');
```

### Post ###
```
  public function store(Request $request)
    {
        $newTodo= new Todos();
        $newTodo->Title = $request->input('Title');
        $newTodo->save();
    }

	
 <form action="{{route('todos.update',$upTodo)}}" method="POST">
    <input type="hidden" name="_method" value="PUT">
    @csrf
					


<a href="{{ route('todos.create')}}" id="btnNew" class="btn btn-dark btn-sm">

```