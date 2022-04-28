### step-by-step-laravel-card-view-use-mysql
step by step laravel card view use mysql

## Data Migrations & Seeding

#1. make migration file
on terminal
```
php artisan make:model Product -m
```
note : Product is name of page


#2. Create Schema for input table Product on Mysql

app/database/migrations/...create_product_table

```
<?php

use Illuminate\Database\Schema\Blueprint;
use Illuminate\Database\Migrations\Migration;

class CreateUtilitesTable extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('products', function (Blueprint $table) {
            $table->increments('id');
            $table->timestamps();
            $table->string('imagePath');
            $table->string('title');
            $table->text('description');
            $table->integer('price');
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::drop('products');
    }
}

```


#3.Create Data Seeder

on terminal
```
php artisan make:seed ProductTableSeeder
```

Create Array
app/Product

```
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Utilites extends Model
{
    protected $fillable = ['imagePath', 'title', 'description', 'price'];
}

```

Create Validity Product

app/database/seeds/ProductTableSeeder.php
```
<?php

use Illuminate\Database\Seeder;

class UtilitesTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        $product = new \App\Product([
            'imagePath' => 'src/img/koeno.jpg',
            'title' => 'Harry Potter',
            'description' => 'Super cool - at least as a child.',
        ]);
        $product->save();
    }
}

```
