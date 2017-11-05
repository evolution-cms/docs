
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Selector</h2>

<p>Скачивать здесь: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Pathologic/Selector" rel="nofollow" target="_blank">Pathologic</a></p>
<p>Selector является заменой для <a href="129.html" title="mm_ddSelectDocuments" target="_blank">mm_ddSelectDocuments</a>.</p>
<p>В отличие от mm_ddSelectDocuments:</p>
<ul>
	<li>уживается с SimpleGallery;</li>
	<li>благодаря DocLister позволяет выбирать данные для списка как угодно и откуда угодно;</li>
	<li>список результатов поиска можно оформлять по-всякому (реализовано с помощью prepare в DocLister);</li>
	<li>код полностью открыт (была мысль разобраться в конфликте mm_ddSelectDocuments с SimpleGallery, но минифицированный js сразу же отбил желание).</li>
</ul>
<p>Код получился простой, разобраться при желании не сложно.</p>
<p>Для работы требуется DocLister.</p>
<p>Больше и нечего написать про этот компонент, разве что некоторых пояснений требует процесс настройки под себя. Сразу поясню на примере.</p>
<p>Допустим, есть tv-параметр c названием related, для хранения списка похожих товаров. Чтобы его поведение отличалось от базового, нужно создать в файле assets/tvs/selector/lib/related.controller.class.php класс:</p>
<pre class="brush: php;">
&lt;?php namespace Selector;
include_once(MODX_BASE_PATH.'assets/tvs/selector/lib/controller.class.php');
class RelatedController extends SelectorController {
... //переопределяем что нужно
}
</pre>

<p>В большинстве случаев, думаю, будет достаточно изменить свойство dlParams, в котором хранятся параметры по умолчанию для запуска DocLister:</p>
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
<p>Если эта часть не понятна, то могу посоветовать обратиться сюда: <a href="https://bezumkin.ru/training/course3/" rel="nofollow" target="_blank">bezumkin</a></p>
<p>Следует обратить внимание, что параметр – related, название файла – related.controller.class.php, а название класса – RelatedController (с большой буквы).</p>
<p>Можно также подгружать нужный класс вручную с помощью плагина на OnManagerPageInit. В этом случае значение имеет только правильное название класса. Также есть ограничение на название tv-параметра: допускаются только латинские буквы и символ подчеркивания.</p>