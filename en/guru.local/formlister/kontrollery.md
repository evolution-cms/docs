
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>FormLister: Контроллеры</h2>

<p>Контроллер представляет собой класс, унаследованный от базового класса \FormLister\Core, который реализует:</p>
<ul>
	<li>загрузку классов для валидации и генерации капчи;</li>
	<li>работу с данными (под данными здесь и далее подразумеваются значения свойства formData, то есть не только значения массива $_REQUEST);</li>
	<li>работу с шаблоном формы и шаблоном успешной обработки.</li>
</ul>
<p>Схема работы:</p>
<ol>
	<li>Загрузка данных из формы</li>
	<li>Загрузка данных из внешних источников</li>
	<li>Вызов сниппетов для обработки данных.</li>
	<li>Валидация данных - если получены данные из формы;</li>
	<li>Вызов сниппетов для обработки данных.</li>
	<li>Итоговая обработка - если получены данные из формы и пройдена валидация.</li>
	<li>Вывод.</li>
</ol>
<p>Итоговая обработка формы происходит в методе process() контроллера. После успешной обработки необходимо установить флаг результа обработки формы с помощью метода setFormStatus(), а также и указать в свойстве renderTpl шаблон для вывода информации с результатами обработки.</p>
<p>Ниже перечислены базовые контроллеры.</p>
<h3><a href="formlister/index.html#otpravka-pisem">Контроллер Form</a> <small>Отправляет письма с данными формы.</small></h3>
<h3><a href="formlister/index.html#avtorizaciya-polzovatelej">Контроллер Login</a> <small>Авторизует пользователя в контексте web.</small></h3>
<h3><a href="formlister/index.html#registraciya-polzovatelej">Контроллер Register</a> <small>Создает web-пользователя и отправляет соответствующие письма.</small></h3>
<h3><a href="formlister/index.html#aktivaciya-uchetnyh-zapisej">Контроллер Activate</a> <small>Обрабатывает ссылку из письма с подтверждением регистрации или отправляет такое письмо.</small></h3>
<h3><a href="formlister/index.html#redaktirovanie-profilya-polzovatelya">Контроллер Profile</a> <small>Предназначен для редактирования данных web-пользователя.</small></h3>
<h3><a href="formlister/index.html#udalenie-profilya-polzovatelya">Контроллер DeleteUser</a> <small>Позволяет пользователям удалять свои учетные записи. Для подтверждения запрашивает пароль.</small></h3>
<h3><a href="formlister/index.html#vosstanovlenie-parolej-polzovatelyami">Контроллер Reminder</a> <small>Предназначен для восстановления паролей web-пользователями.</small></h3>
<h3><a href="formlister/index.html#sozdanie-i-redaktirovanie-dokumentov-polzovatelyami">Контроллер Content</a> <small>Позволяет создавать и изменять записи с помощью классов MODxAPI.</small></h3>
<h3><a href="formlister/index.html#udalenie-dokumentov-polzovatelyami">Контроллер DeleteContent</a> <small>Позволяет пользователям удалять созданные ими записи.</small></h3>
<h3>Контроллер MailChimp <small>Добавляет пользователей в список рассылки сервиса MailChimp. Добавлен как пример расширения базового класса \FormLister\Core.</small></h3>