Инструкции Switch можно создавать с помощью директив @`switch`, `@case`, и `@break:`, `@default`, `@endswitch`

```blade
@switch($i)
    @case(1)
        Первый случай...
        @break
    
    @case(2)
        Второй случай...
        @break

    @default
        Типичный случай...
@endswitch
```