> [!IMPORTANT]  
> Команди не виконуються в автоматичному режимі якщо сайт переведено в режим обслуговування (Конфігурація -> Сайт -> Статус сайта -> Оффлайн).

Щоб команди виконувались в автоматичному режимі на стороні сервера без участі розробника використовується Розклад.

Для налаштування розкладу, потрібно в файл команди додати метод `schedule()`.
```
/**
 * Define the command's schedule.
 *
 * @param  \Illuminate\Console\Scheduling\Schedule  $schedule
 * @return void
 */
public function schedule(Schedule $schedule)
{
   $schedule->command(static::class)->everyFiveMinutes();
}
```

В методі `boot()` сервіс провайдера ініціалізувати розклад.
```
if (count($this->commands)) {
    $this->app->booted(function () {
        $this->defineConsoleSchedule();
    });
}
```

Додати необхідні методи в файл сервіс провайдера
```
/**
 * Define the application's command schedule.
 *
 * @note check timezones list timezone_identifiers_list()
 *
 * @return void
 */
protected function defineConsoleSchedule()
{
    $this->app->singleton(Schedule::class, function ($app) {
        return tap(new Schedule(now()->timezoneName), function ($schedule) {
            $this->schedule($schedule->useCache('file'));
        });
    });
}

/**
 * Define the application's command schedule.
 *
 * @param  \Illuminate\Console\Scheduling\Schedule  $schedule
 * @return void
 */
public function schedule(Schedule $schedule)
{
    foreach ($this->commands as $command) {
        (new $command)->schedule($schedule);
    }
}
```

Налаштувати запуск крон
```
* * * * * cd /path-to-your-project/core && php artisan schedule:run >> /dev/null 2>&1
```

Детальніше тут https://laravel.com/docs/9.x/scheduling
