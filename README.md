<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## STEP BY STEP GUIDE

Chirper is a microblogging platform that I got from [Laravel Bootcamp](https://bootcamp.laravel.com/). It was a way for me to immediately get familiarized with Laravel, and I learned a lot from this project. I used the Blade template because I see it in a lot of existing Laravel projects. Below is the ordered list of commands I used to create the project from start to finish:

## Installation

1. Create a laravel project:
      ```bash
      composer create-project laravel/laravel chirper

2. Navigate to the project directory:
      ```bash
      cd chirper

3. Start the project:
      ```bash
      php artisan serve

4. Configure the database in .env:
      ```bash
      DB_DATABASE=laravel
      DB_USERNAME=xxx
      DB_PASSWORD=xxx

5. Install laravel breeze:
      ```bash
      composer require laravel/breeze --dev
      php artisan breeze:install blade

6. In another terminal, run dev:
      ```bash
      npm run dev

7. Migrate everything to database
      ```bash
      php artisan migrate

## Creating Chirps

1. Create a model with migration and resource controller:
      ```bash
      php artisan make:model -mrc Chirp

2. Create routing in web.php to connect to (index) and (store).
3. Create a function in ChirpController::index that points to a view.
4. Make a blade template for (index). 
5. Create a function in ChirpController::store that has validation and DB create.
6. Declare that User model hasMany relationship with Chirp model.
7. Put (fillable) in Chirp model to allow mass assignment.
8. Fill up chirps migration table with columns.

9. Migrate everything to database
      ```bash
      php artisan migrate

10. Use tinker for DB debugging (Optional)
      ```bash
      php artisan tinker

## Showing Chirps

1. Update ChirpController::index with array data that points to database.
2. Declare that Chirp model belongsTo User model.
3. Update index.blade to have a for-loop that will display data from the database.

## Editing Chirps

1. Add edit and update routes in the ChirpController.
    - EDIT = shows the form
    - UPDATE = accepts data
2. Update index.blade to have an edit button.
3. Update the edit and update function inside ChirpController to display and receive data.

4. Make a Form Validation Request to reduce redundant data:
      ```bash
      php artisan make:request ValidationName

5. Make authorization for security:
      ```bash
      php artisan make:policy ChirpPolicy --model=Chirp

6. Write authorization for who can access the data inside ChirpPolicy::update.

## Deleting Chirps

1. Add destroy route in the ChirpController.
2. Update the delete function inside ChirpController.
3. Update delete function in the ChirpPolicy.
4. Update index.blade to have a delete button.

## Notifications and Events

1. Create a notification:
      ```bash
      php artisan make:notification NewChirp

2. Update NewChirp::toMail to include subject, greeting, and line

3. Make an event:
      ```bash
      php artisan make:event ChirpCreated

4. Add Chirp model inside the parameter of __construct
5. create $dispatchesEvents in Chirp model

6. Create Event Listener:
      ```bash
      php artisan make:listener SendChirpCreatedNotifications --event=ChirpCreated

7. Implement ShouldQueue in the event listener
8. Add the event listener to EventServiceProvider::class

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
