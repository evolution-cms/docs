
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>eForm: Защита от спама</h2>

<p>Встроенная капча не дает надежной защиты от спама. Поэтому от нее имеет смысл или отказаться вообще в пользу других решений или использовать несколько методов борьбы со спамом одновременно. В данный момент популярно решение, используемое в чанке <span class="text-bold">eFeedbackForm</span> кастомной сборке Дмитрия Лукьяненко. Суть метода - добавить в шаблон формы скрытое поле и сделать его незаполнение обязательным:</p>
<pre class="brush: html;">&lt;input value="" name="special" class="special" type="text" eform="Спец:date:0" style="display:none;"&gt;</pre>
<h3>Код чанка eFeedbackForm</h3>
<pre class="brush: html;">
&lt;p>&lt;span style="color:#900;">[+validationmessage+]&lt;/span>&lt;/p>
&lt;form  class="eform" method="post" action="[~[*id*]~]">
	&lt;input type="hidden" name="formid" value="feedbackForm" />
	&lt;input value="" name="special" class="special" type="text" eform="Спец:date:0"  style="display:none;" />
	&lt;p>
		&lt;input type="text" name="name" id="name" class="grid_3" value=""  eform="Имя:string:1"/>
		&lt;label for="name">Ваше имя&lt;/label>
	&lt;/p>
	&lt;p>
		&lt;input type="text" name="email" id="email" class="grid_3" value="" eform="E-mail:email:1" />
		&lt;label for="email">Ваш E-mail&lt;/label>
	&lt;/p>
	&lt;p>
		&lt;input type="text" name="phone" id="subject" class="grid_3" value="" eform="Номер телефона:string:1"/>
		&lt;label for="subject">Номер телефона&lt;/label>
	&lt;/p>
	&lt;p>
		&lt;textarea name="comments" id="message" class="grid_6" cols="50" rows="10" eform="Текст сообщения:string:1">&lt;/textarea>
	&lt;/p>
	&lt;p>Введите код с картинки: &lt;br />
		&lt;input type="text" class="ver" name="vericode" />&lt;img class="feed" src="[+verimageurl+]" alt="Введите код" />
	&lt;/p>            
	&lt;p>
		&lt;input type="submit" name="submit" class="subeform grid_2" value="Отправить сообщение"/>
	&lt;/p>
&lt;/form>
</pre>