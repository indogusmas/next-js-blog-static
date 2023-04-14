---
title: 'Crud Api Laravel 9 Part 1'
excerpt: 'Laravel is popular framework for php developer. This tutorial i try share about how to CRUD api laravel.'
coverImage: '/assets/blog/laravel/laravel.jpg'
date: '2020-03-16T05:35:07.322Z'
author:
  name: Indo Gusmas
  picture: '/assets/blog/authors/icon_person.png'
ogImage:
  url: '/assets/blog/preview/cover.jpg'
---

## Step 1: Install Laravel.
First, you'll need to install Laravel on your local development environment. You can do this using Composer, a PHP dependency management tool. Open your terminal and run the following command:

```
composer global require laravel/installer
```

This will install the latest version of Laravel on your system.

## Step 2: Create a New Laravel Project.
Once Laravel is installed, you can create a new Laravel project by running the following command:

```
laravel new my-api
```
Replace "my-api" with the name of your project. This will create a new Laravel project with the name "my-api" in a directory with the same name.

## Step 3: Configure Your Database
Next, you'll need to configure your database. Open the .env file in the root of your Laravel project and update the following lines with your database details:

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=my_database
DB_USERNAME=my_username
DB_PASSWORD=my_password
```
Replace "my_database", "my_username", and "my_password" with your actual database details.

## Step 4: Create a Model
In Laravel, a model represents a database table and is used to interact with the data in the table. Let's create a model for a simple "Task" resource. Run the following command:

```
php artisan make:model Task --migration
```

This will create a model file in the app directory and a migration file in the database/migrations directory.

## Step 5: Define the Model and Migration
Open the app/Task.php file and define the model as follows:

```
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Task extends Model
{
    protected $fillable = ['title', 'description'];
}
```

This defines a Task model with two fillable fields: title and description.

Next, open the migration file in the database/migrations directory and define the migration as follows:

```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class CreateTasksTable extends Migration
{
    public function up()
    {
        Schema::create('tasks', function (Blueprint $table) {
            $table->id();
            $table->string('title');
            $table->text('description');
            $table->timestamps();
        });
    }

    public function down()
    {
        Schema::dropIfExists('tasks');
    }
}
```
This migration creates a tasks table with an id, title, description, and timestamps columns.
## Step 6: Run Migrations
Next, you'll need to run the migrations to create the tasks table in your database. Run the following command:
```
php artisan migrate
```

This will create the tasks table in your database.

## Step 7: Create API Routes
In Laravel, routes define the endpoints for your API. Open the routes/api.php file and define the API routes as follows:

```
<?php

use App\Http\Controllers\TaskController;
use Illuminate\Support\Facades\Route;

Route::apiResource('tasks', TaskController::class);

```
This defines a RESTful API resource route for the Task model that maps to the TaskController class.

## Step 8: Create a Controller
A controller handles the business logic of your API. Let's create a TaskController that will handle CRUD operations for the Task model. Run the following command:

```
php artisan make
```

See you on Part 2