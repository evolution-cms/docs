Інструкції Switch можна створювати за допомогою директив @`switch`, `@case`, і` @break:`, `@default`, `@endswitch`

```blade
@switch($i)
    @case(1)
        Перший випадок...
        @break

    @case(2)
        Другий випадок...
        @break

    @default
        Типовий випадок...
@endswitch
```