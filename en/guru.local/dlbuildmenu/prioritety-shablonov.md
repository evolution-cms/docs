
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLBuildMenu: Шпаргалка по приоритетам шаблонов</h2>

<p>Система шаблонов DLBuildMenu действительно очень гибкая, но к ней нужно привыкнуть. Для упрощения задачи ниже привожу cheatsheet (шпаргалку) по приоритетам шаблонов.</p>
<p>В левой колонке перечислены типы элементов меню, а справа от каждого элемента идут применяемые для него шаблоны в порядке убывания приоритета.</p>
<div class="table-responsive">
	<table class="table table-vcenter table-condensed table-bordered table-hover">
		<thead>
			<tr>
				<th>Тип элемента меню</th>
				<th>Высший приоритет</th>
				<th>Приоритет 1</th>
				<th>Приоритет 2</th>
				<th>Приоритет 3</th>
				<th>Приоритет 4</th>
				<th>Приоритет 5</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Обёртка для всего меню (уровень 1)</td>
				<td>&amp;TplOwner1</td>
				<td>&amp;TplMainOwner</td>
				<td>дефолтное значение &amp;TplMainOwner</td>
				<td></td>
				<td></td>
				<td></td>
			</tr>
			<tr>
				<td>Обёртка для суб-меню (уровень N равен 2 и более)</td>
				<td>&amp;TplOwnerN</td>
				<td>&amp;TplSubOwner</td>
				<td>дефолтное значение &amp;TplSubOwner</td>
				<td></td>
				<td></td>
				<td></td>
			</tr>
			<tr>
				<td>Не текущий пункт меню с дочерними (любой уровень N)</td>
				<td>&amp;TplDepthN</td>
				<td>&amp;TplOneItem</td>
				<td>дефолтное значение &amp;TplOneItem</td>
				<td></td>
				<td></td>
				<td></td>
			</tr>
			<tr>
				<td>Не текущий пункт меню без дочерних (любой уровень N)</td>
				<td>&amp;TplNoChildrenDepthN</td>
				<td>&amp;noChildrenRowTPL</td>
				<td>&amp;TplDepthN</td>
				<td>&amp;TplOneItem</td>
				<td>дефолтное значение &amp;TplOneItem</td>
				<td></td>
			</tr>
			<tr>
				<td>Текущий пункт меню с дочерними (любой уровень N)</td>
				<td>&amp;TplCurrentN</td>
				<td>&amp;TplCurrent</td>
				<td>&amp;TplDepthN</td>
				<td>&amp;TplOneItem</td>
				<td>дефолтное значение &amp;TplOneItem</td>
				<td></td>
			</tr>
			<tr>
				<td>Текущий пункт меню без дочерних (любой уровень N)</td>
				<td>&amp;TplCurrentNoChildrenN</td>
				<td>&amp;TplNoChildrenDepthN</td>
				<td>&amp;noChildrenRowTPL</td>
				<td>&amp;TplDepthN</td>
				<td>&amp;TplOneItem</td>
				<td>дефолтное значение &amp;TplOneItem</td>
			</tr>
		</tbody>
	</table>