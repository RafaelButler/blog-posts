## Using Traits in Laravel Practically

To be straightforward, a trait consists of a way to reuse code in a single inheritance language like PHP.

An example of this is when we have a set of functions that we want to use in classes that are independent of each other.

A `trait` (translated from English as 'characteristic') behaves like a class but cannot be instantiated. The objective is a group of functionalities to share.

Let's see a very simple example:

```php
trait Tags {
	function attachTag() {}
}

class Post {
	use Tags;
}

$post = new Post::class;
$post->attachTag();

```

This is indeed a very cool feature of PHP that allows us great flexibility.

But our goal is to discuss the use of traits in Laravel.

## And when should we use them?

There are several specific situations where you will frequently encounter the use of traits in the framework.

They are:

- Reusing functions
- Common relationships between models
- Extending Trait behavior

Of course, there are other ways to use them, but we won't be able to cover everything here. Let's have an overview of these three points.

Let's go!

## Reusing functions

As we can see in the Laravel documentation, notifications can be sent in two ways.

Using the Notification Facade or we can use the Notifiable trait that comes by default in the User model class

```php
class User extends Authenticatable
{
    use Notifiable;
}
```

From this point on, we have access to a `notify()` method that receives a notification instance.

```php
$user->notify(new InvoicePaid($invoice));
```

We can use the _Notifiable_ trait in any other class we want.

## Common relationships between models

We often have relationships across multiple models. One package that we can see how this works in practice is [laravel-permission](<[https://spatie.be/docs/laravel-permission/v5/introduction](https://spatie.be/docs/laravel-permission/v5/introduction)>)

```php
public function roles(): BelongsToMany
{
    $relation = $this->morphToMany(
        config('permission.models.role'),
        'model',
        config('permission.table_names.model_has_roles'),
        config('permission.column_names.model_morph_key'),
        app(PermissionRegistrar::class)->pivotRole
    );

    if (! app(PermissionRegistrar::class)->teams) {
        return $relation;
    }

    return $relation->wherePivot(app(PermissionRegistrar::class)->teamsKey, getPermissionsTeamId())
        ->where(function ($q) {
            $teamField = config('permission.table_names.roles').'.'.app(PermissionRegistrar::class)->teamsKey;
            $q->whereNull($teamField)->orWhere($teamField, getPermissionsTeamId());
        });
}
```

This means that any model that uses the trait will have access to the `roles()` relationship.

## Extending Trait Behavior

We can take the simple example we made earlier to explain this point.

```php
trait Tags {
	function attachTag() {}
}
```

We use it in the class we want, and override the desired method.

```php
class Post {
	use Tags;

	function attachTag() {
		// Escreve a logica toda aqui
	}
}
```

## Conclusion

There are many ways to make our codes reusable and readable. You can find many more examples of how to use them in the php [doc](<[https://www.php.net/manual/en_US/language.oop5.traits.php](https://www.php.net/manual/en_US/language.oop5.traits.php)>).

You can also take a look at the [Laravel](<[https://laravel.com/](https://laravel.com/)>) documentation.
