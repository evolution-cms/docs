Blade is a simple yet powerful templating engine built into Evolution CMS. Unlike some PHP templating engines, Blade doesn't restrict you from using plain PHP code in your templates. In fact, all Blade templates are compiled into plain PHP code and cached until they are changed, meaning Blade adds virtually no overhead to your application. Blade template files use the `.blade.php` file extension and are usually stored in the `/views/` directory.

## Display data

You can display the data that is passed to your Blade views by enclosing a variable in curly braces. For example, you can display the contents of the `name` variable like this:

```blade
Hello {{ $name }}.
```

> **Note**  
> Blade `{{ }}` echo expressions are automatically sent via PHP's `htmlspecialchars` function to prevent XSS attacks.

You are not limited to displaying the contents of variables passed to the view. You can also iterate over the results of any PHP function. In fact, you can put any PHP code you want inside the Blade echo statement:

```blade
Current UNIX timestamp {{ time() }}.
```

### Displaying unshielded data

By default, `{{ }}` Blade statements are automatically sent through PHP's `htmlspecialchars` function to prevent XSS attacks. If you don't want your data to be escaped, you can use the following syntax:

```blade
Hello, {!! $name !!}.
```

> **Warning**  
> Be very careful when reproducing content provided by users of your app. Normally, you should use escaped double curly braces syntax to prevent XSS attacks when displaying user-supplied data.

### Blade and JavaScript

Since many JavaScript frameworks also use curly braces to indicate that a given expression should be rendered in the browser, you can use the `@` symbol to tell the Blade rendering engine that the expression should be left untouched. Example:

```blade
<h1>Evolution CMS</h1>

Hi @{{ $name }}.
```

In this example, the @symbol will be removed from Blade, but the `{{ name }}` expression will remain untouched by the Blade handler, allowing it to be rendered in your JavaScript structure.

The `@` character can also be used to escape Blade directives:

```blade
{{-- Blade template --}}
@@if()

<!-- HTML output -->
@if()
```

#### JSON visualization

Sometimes you can pass an array to your view with the intention of displaying it as JSON to initialize a JavaScript variable. Example:

```blade
<script>
     var app = <?php echo json_encode($array); ?>;
</script>
```

However, instead of calling `json_encode` manually, you can use the `Js::from` method. The `from` method takes the same arguments as PHP's `json_encode` function, but this will ensure that the resulting JSON is properly escaped for HTML quoting. The `from` method will return a string `JSON.parse` JavaScript operator that will convert the given object or array into a valid JavaScript object:

```blade
<script>
     var app = {{ Js::from($array) }};
</script>
```

> **Warning**  
> You should only use the `Js::from` method to render existing variables as JSON. The Blade pattern is based on regular expressions, and attempts to pass a complex expression to a directive can cause unexpected errors.

#### The `@verbatim` directive

If you expose JavaScript variables in a large part of your template, you can wrap the HTML in the `@verbati` directive so that you don't have to append the `@` symbol to each Blade echo statement:

```blade
@verbatim
     <div class="container">
         Hello {{ $name }}.
     </div>
@endverbatim
```

## Blade Directives

In addition to template inheritance and data mapping, Blade also provides convenient shortcuts for common PHP control structures such as conditional statements and loops. These shortcuts provide a very clean, concise way of working with PHP control structures while remaining familiar to their PHP counterparts.