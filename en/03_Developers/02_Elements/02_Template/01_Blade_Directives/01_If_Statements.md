You can create `if' operators using `@if`, `@elseif`, `@else` and `@endif` directives. These directives function identically to their PHP counterparts:

```blade
@if (count($records) === 1)
     I have one record!
@elseif (count($records) > 1)
     I have many records!
@else
     I have no records!
@endif
```

For convenience, Blade also provides the `@unless` directive:

```blade
@unless (evo_role())
     You are not logged in, so your role on the site is not defined.
@endunless
```

In addition to the conditional directives already discussed, the `@isset` and `@empty` directives can be used as convenient shortcuts for the corresponding PHP functions:

```blade
@isset($records)
     // $records is defined and not null...
@endisset

@empty($records)
     // $records is "empty"...
@endempty
```