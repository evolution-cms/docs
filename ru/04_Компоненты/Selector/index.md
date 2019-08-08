Selector - custom TV для составления списка документов в Evolution CMS.
<p>Selector является заменой для mm_ddSelectDocuments.</p>
<p>В отличие от mm_ddSelectDocuments:</p>
<ul>
	<li>уживается с SimpleGallery;</li>
	<li>благодаря DocLister позволяет выбирать данные для списка как угодно и откуда угодно;</li>
	<li>список результатов поиска можно оформлять по-всякому (реализовано с помощью prepare в DocLister);</li>
	<li>код полностью открыт.</li>
</ul>
<p>Для работы требуется DocLister.</p>

<p>После установки дополнения из магазина приложений необходимо у нужного TV параметра авбрать тип ввода "selector".</p>
<p>Компонент требует некой настройки под себя.</p>

<p>Допустим, есть tv-параметр c названием `related`, для хранения списка похожих товаров. Чтобы его поведение отличалось от базового, нужно создать в файле `assets/tvs/selector/lib/related.controller.class.php` класс:</p>
<pre class="brush: php;">
&lt;?php namespace Selector;
include_once(MODX_BASE_PATH.'assets/tvs/selector/lib/controller.class.php');
class RelatedController extends SelectorController {
... //переопределяем что нужно
}
</pre>

<p>В большинстве случаев  будет достаточно изменить свойство dlParams, в котором хранятся параметры по умолчанию для запуска DocLister:</p>
<pre class="brush: php;">
&lt;?php namespace Selector;
include_once(MODX_BASE_PATH.'assets/tvs/selector/lib/controller.class.php');
class RelatedController extends SelectorController {
    public function __construct($modx) {
        parent::__construct($modx);
        $this-&gt;dlParams['parents'] = 5;
        $this-&gt;dlParams['addWhereList'] = 'c.published = 1';
    }
}
</pre>

<p>Следует обратить внимание, что параметр – `related`, название файла – `related.controller.class.php`, а название класса – `RelatedController` (с большой буквы).</p>
<p>Можно подгружать нужный класс вручную с помощью плагина на OnManagerPageInit. В этом случае значение имеет только правильное название класса. Также есть ограничение на название tv-параметра: допускаются только латинские буквы и символ подчеркивания.</p>
