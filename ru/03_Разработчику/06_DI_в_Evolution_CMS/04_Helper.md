### Helper ###
Здесь собраны различные методы которые помогают в разработке

- phpThumb - используется для сжатия картинок. Все передаваемые аргументы точно такие же как в сниппете [phpthumb](../../04_Компоненты/phpthumb/index.md)

Пример использования

```blade
<img src="{{\Helper::phpThumb('assets/images/evo-logo.png', 'w=150,h=76,far=C,bg=FFFFFF')}}" >
```

- Mailer - отправка писем с помощью встроенного сервиса.

Пример использования
```php
$evo = EvolutionCMS();

// подключить Mailer если нужно
include_once(MODX_BASE_PATH.'assets/lib/Helpers/Mailer.php');

$debug = true;
$cfg = [];

// обязательно to
$cfg['to'] = 'vasya@rambler.ru';

// если не указывать From и FromName, то используются данные из настроек сайта
$cfg['From'] = 'vasya@yandex.ru';
$cfg['FromName'] = 'Василий Пупкин';

// дополнительные адреса reply-to, cc, bcc
// $cfg['replyTo'] = 'vasya@gmail.com';
// $cfg['cc'] = '';
// $cfg['bcc'] = '';

$cfg['subject'] = 'Тема письма';

$mail = new \Helpers\Mailer($evo, $cfg, $debug);

$cfg['isHtml'] = 1;
$message = '<p>Добрый день!</p>';

if($mail->send($message)) {
  echo 'Успешно отправлено.';
} else {
  echo 'Ошибка при отправке: '.$mail->ErrorInfo;
}
```
