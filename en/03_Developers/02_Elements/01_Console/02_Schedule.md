> [!IMPORTANT]  
> Commands are not executed automatically if the site is put into maintenance mode (Configuration -> Site -> Site Status -> Offline).

In order for the commands to be executed automatically on the server side without the involvement of the developer, the Schedule is used.

To configure the schedule, you need to add the `schedule()` method to the command file.
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

In the `boot()` method, the provider service initializes the schedule.
```
if (count($this->commands)) {
    $this->app->booted(function () {
        $this->defineConsoleSchedule();
    });
}
```

Add the necessary methods to the service provider's file
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

Configure the crown startup
```
* * * * * cd /path-to-your-project/core && php artisan schedule:run >> /dev/null 2>&1
```

More details here https://laravel.com/docs/9.x/scheduling
