
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>ddTypograph: Описание параметров</h2>

<p>Чтобы отключить работу типографа для фрагмента текста, используйте тег <notg><code>&lt;notg&gt;&lt;/notg&gt;</code></notg>, текст внутри него не типографируется.</p>
<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/DivanDesign/MODXEvo.snippet.ddTypograph" rel="nofollow" target="_blank">DivanDesign</a></p>
<table class="table table-bordered table-vcenter">
	<tbody><tr>
		<th>Название</th>
		<th>Описание</th>
		<th>Допустимые значения</th>
		<th>Значение по умолчанию</th>
		</tr>
		<tr>
			<td><span class="text-primary" data-toggle="tooltip" data-placement="right" title="Обязательный параметр">text*</span></td>
			<td colspan="1">Текст, который нужно типографировать.</td>
			<td>{string}</td>
			<td>–</td>
		</tr><tr>
		<td>optAlign</td>
		<td colspan="1">Оптическое выравнивание (висячая пунктуация).</td>
		<td>{0|1}</td>
		<td>0</td>
		</tr><tr>
		<td>text_paragraphs</td>
		<td colspan="1">Простановка параграфов и переносов строк.</td>
		<td>{0|1}</td>
		<td>0</td>
		</tr><tr>
		<td>text_autoLinks</td>
		<td colspan="1">Выделение ссылок из текста (в том числе email).</td>
		<td>{0|1}</td>
		<td>0</td>
		</tr><tr>
		<td>etc_unicodeConvert</td>
		<td colspan="1">Преобразовывать html-сущности в юникод (– вместо <span>&amp;</span>mdash; и т.д.).</td>
		<td>{0|1}</td>
		<td>1</td>
		</tr><tr>
		<td>noTags</td>
		<td colspan="1">Не добавлять теги. Бывают ситуации, когда использование HTML-тегов в тексте недопустимо (например, когда текст выводится в значение атрибута тега), для таких случаев и предназначен этот параметр.</td>
		<td>{0|1}</td>
		<td>0</td>
		</tr>
	</tbody>
</table>