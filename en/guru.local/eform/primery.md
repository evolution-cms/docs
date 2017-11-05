
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>eForm: Примеры</h2>

<h3 class="sub-header text-bold">eForm в модальном окне</h3>
<p>Ситуация, когда надо вывести форму в модальном окне довольно частая. Выведем форму в модальном окне Bootstrap 3.</p>
<p>Модальное окно будет выглядеть примерно так:</p>
<pre class="brush: html;">
<button class="btn" data-toggle="modal" data-target="#myModal"></button>
<div class="modal fade" id="myModal" tabindex="-1" role="dialog" aria-labelledby="myLargeModalLabel" aria-hidden="true">
	<div class="modal-dialog">
		<div class="modal-content">
			<div class="modal-header">
				<button type="button" class="close" data-dismiss="modal" aria-hidden="true">&times;</button>
				<h4 class="modal-title">Заголовок окна</h4>
			</div>
			<div id="myModal_form">
				[!eForm? &formid=`Form` &tpl=`tplForm` &report=`tplReport` &thankyou=`tplThank` &subject=`Сообщение с сайта [(site_name)]`!]
			</div>
		</div>
	</div>
</div>
</pre>
<p>Чанк tplForm:</p>
<pre class="brush: html;">
&lt;form method="post" action="[~[*id*]~]" name="Form" id="Form">
	<div class="modal-body">
		<input value="" name="special" class="special" type="text" eform="Спец:date:0" style="display:none;">
		...
	</div>
	<div class="modal-footer">
		<input type="submit" class="btn" name="submit" id="submit" value=" Отправить ">
	</div>
&lt;/form>
</pre>
<p>Чанк tplThank:</p>
<pre class="brush: html;">
<div class="modal-body">Ваше сообщение отправлено.</div>
<div class="modal-footer">
	<button type="button" class="btn btn-default" data-dismiss="modal">Закрыть</button>
</div>
</pre>
<p>Ну и последний штрих, нужно разместить примерно такой скрипт:</p>
<pre class="brush: javascript;">
&lt;script>
	$(function(){
		$(document).on("submit","#Form",function(e){
			e.preventDefault();
			var m_method=$(this).attr('method');
			var m_action=$(this).attr('action');
			var m_data=$(this).serialize();
			$.ajax({
				type: m_method,
				url: m_action,
				data: m_data,
				resetForm: 'true',
				success: function(result){
					var data = $(result).find("#myModal_form").html();
					$("#myModal_form").html(data);
				}
			});
		});
	});
&lt;/script>
</pre>

<h3 class="sub-header text-bold">eForm Ajax Submit</h3>
<p>Создаем примерно такой вызов eForm, обернут в диве с id <code>ajaxContactForm</code> - обротите внимание что по этому id и будет вся привязка.</p>
<p>Тут конечно можно ставить сразу форму без вызова через eForm, её же полюбому оброботает плагин.</p>
<p><code>[(cfg_from)], [(cfg_email)]</code> - ТВ переменные сайта сохранённые в системной таблицы с помощью плагина <a href="cfgtv/index.html" title="MODx CfgTv">CfgTv</a>.</p>
<pre class="brush: html;">
<div id="ajaxContactForm">
	[!eForm?
	&formid=`contactForm`
	&subject=`Сообщение с сайта [(site_name)]`
	&tpl=`formTpl`
	&errorTpl=`errorTpl`
	&report=`reportTpl`
	&thankyou=`thankyouTpl`
	&gotoid=`244`
	&vericode=`0`
	&from=`[(cfg_from)]`
	&to=`[(cfg_email)]`
	!]
</div>
</pre>
<p>Скрипт Ajax обработки</p>
<pre class="brush: javascript;">
<script type="text/javascript">
	$(document).on('submit','#ajaxContactForm form',function(e){
		$.ajax({
			type: 'post',
			url: '/ajaxContactForm',
			data: $(this).serialize(),
			success: function(data){
				$('#ajaxContactForm form').remove();
				$('#ajaxContactForm').html(data); 
			}
		});
		e.preventDefault();
	});
</script>
</pre>
<p>Создаем плагин например <span class="text-bold">AjaxSubmit</span> который срабатывает на событие <code>OnPageNotFound</code></p>
<pre class="brush: php;">
switch($_GET['q']){
	case 'ajaxContactForm':
		echo $modx->runSnippet(
			'eForm',
			array(
				'formid' => 'contactForm',
				'subject' => 'Сообщение с сайта [(site_name)]',
				'tpl' => 'formTpl',
				'report' => 'reportTpl',
				'thankyou' => 'thankyouTpl',
				'errorTpl' => 'errorTpl',
				'vericode' => 0,
				'protectSubmit' => '0',
				'from' => '[(cfg_from)]',
				'to' => '[(cfg_email)]'
			)
		);
		die();
	break;
}
</pre>