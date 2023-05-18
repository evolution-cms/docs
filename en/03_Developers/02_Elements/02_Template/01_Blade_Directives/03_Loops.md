In addition to conditional statements, Blade provides simple directives for working with PHP's loop structures. Again, each of these directives functions identically to their PHP counterparts:

```blade
@for ($i = 0; $i < 10; $i++)
     Current value is {{ $i }}
@endfor

@foreach ($users as $user)
     <p>This is user {{ $user->id }}</p>
@endforeach

@forelse ($users as $user)
     <li>{{ $user->name }}</li>
@empty
     <p>No users</p>
@endforelse

@while (true)
     <p>I loop forever.I loop forever.</p>
@endwhile
```

> **Note**  
> When iterating through a foreach loop, you can use [the-loop-variable](#the-loop-variable) to get valuable information about the loop, such as whether you are on the first or last iteration of the loop.

When using loops, you can also skip the current iteration or end the loop using `@continue` and `@break` directives:

```blade
@foreach ($users as $user)
     @if ($user->type == 1)
         @continue
     @endif

     <li>{{ $user->name }}</li>

     @if ($user->number == 5)
         @break
     @endif
@endforeach
```

You can also include a continue or break condition in the directive declaration:
```blade
@foreach ($users as $user)
     @continue($user->type == 1)
         <li>{{ $user->name }}</li>
     @break($user->number == 5)
@endforeach
```

<a name="the-loop-variable"></a>
### Loop variable

During `foreach' traversal of the `$loop` loop, the variable will be accessible inside the loop. This variable provides access to some useful information, such as the current loop index and whether this is the first or last iteration of the loop:

```blade
@foreach ($users as $user)
     @if ($loop->first)
         This is the first iteration.
     @endif

     @if ($loop->last)
         This is the latest iteration.
     @endif

     <p>This is user {{ $user->id }}</p>
@endforeach
```

If you are inside a nested loop, you can access the `$loop` variable of the parent loop using the `parent` property:

```blade
@foreach ($users as $user)
     @foreach ($user->posts as $post)
         @if ($loop->parent->first)
             This is the first iteration of the parent loop.
         @endif
     @endforeach
@endforeach
```

The `$loop` variable also contains a number of other useful properties:

| Property           | Description                                                   |
|--------------------|---------------------------------------------------------------|
| `$loop->index`     | The index of the current iteration of the loop (starts at 0). |
| `$loop->iteration` | The current iteration of the loop (starting at 1).            |
| `$loop->remaining` | The remaining iterations in the loop.                         |
| `$loop->count`     | The total number of elements in the repeating array.          |
| `$loop->first`     | Is this the first iteration of the loop.                      |
| `$loop->last`      | Is this the last iteration of the loop.                       |
| `$loop->even`      | Is this an even loop iteration.                               |
| `$loop->odd`       | Is this an odd iteration of the loop.                         |
| `$loop->depth`     | Nesting level of the current cycle.                           |
| `$loop->parent`    | When in a nested loop, the parent loop variable.              |