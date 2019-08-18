
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLSiblings: Вывод соседних ресурсов с шаблонизацией </h2>

Вывод соседних ресурсов с шаблонизацией (множественная кольцевая перелинковка).

<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Aharito/DLSiblings" rel="nofollow" target="_blank">Aharito</a></p>

<strong>DLSiblings</strong> — сниппет вывода соседних ресурсов для Evolution CMS (MODx Evo). Предназначен для организации множественной кольцевой перелинковки страниц сайта. Основан на сниппете <strong>DocLister</strong>, поэтому можно использовать все возможности ДокЛистера.

<h3>Немного теории</h3>
Что такое множественная кольцевая перелинковка? Сеошники наверняка знают о ней. А для тех, кто не знает — это схема перелинковки страниц сайта, позволяющая неплохо поднять сайт по низкочастотным и СНЧ запросам.

<em>*** Подробнее о кольцевой перелинковке читайте в моей статье: <a href="https://aharito.ru/seo-prodvizhenie/shema-perelinkovki-stranic-sajta-pod-nch">Схема перелинковки сайта под НЧ</a></em>

<h3>Параметры сниппета</h3>
<ul>
<li><strong>&renderSnippet</strong> ( DocLister | sgController ) сниппет, используемый для вывода, default DocLister</li>
    <li><strong>&prevQty</strong> - Кол-во выводимых соседей-предшественников, default 2</li>
    <li><strong>&nextQty</strong> - Кол-во выводимых соседей-последователей, default 2</li>
    <li><strong>все</strong> остальные параметры и шаблоны как в DocLister</li>
</ul>

Можно использовать унаследованные от DocLister (такие же, как у него): условия выборки &addWhereList и &filters, условия сортировки &orderBy, глубину выборки &depth, prepare-сниппеты и многие другие параметры и все шаблоны.

Если в качестве сниппета вывода указан sgController, то соответственно можно использовать и все условия, параметры и шаблоны sgController.

<h5>Шаблоны сниппета</h5>
Все шаблоны - точно такие же, как у DocLister. Плейсхолдеры в шаблонах - тоже точно такие же, как в DocLister. Если в качестве сниппета вывода указан sgController, то шаблоны и плейсхолдеры - точно такие же, как в sgController.

<h3>Установка</h3>
<ul>
    <li>Сниппет находится <a href="https://github.com/Aharito/DLSiblings">на Гитхабе</a></li>
    <li>Архив нужно <a href="https://github.com/Aharito/DLSiblings/archive/master.zip">скачать</a> и установить через Extras ("Установка из архива").</li>
</ul>

<h3>Пример</h3>

	[[DLSiblings?
		&idType=`parents`
		&parents=`[*parent*]`
		&tpl=`@CODE: <a href="[+url+]">[+tv.h1+]</a><br>`
		&prevQty=`2`
		&nextQty=`2`
		&tvList=`h1`
	]]



<em>*** Больше примеров с кодом и пояснениями в моей статье: <a href="https://aharito.ru/modx-evolution/dlsiblings-primery-perelinkovki">Примеры применения DLSiblings</a></em>

<h3>Результат работы</h3>
В этом примере параметром &parents мы задаем выборку, в которой будем искать соседей — все документы, находящиеся в той же папке, что и текущий.

Результатом работы будет список ссылок на статьи, соседние по ИД для текущей.

<img src="https://lh3.googleusercontent.com/0NDlBaOvEdAXJ8TYEn5JPDRlAYYK4Q3xBA6hzDAdABVXlQAPHwEaSTfxYOgj81HOQXPfrhbQGuE7ihiLpmrr_ew4wGnG_8NTl0OkyS6F-h9tGxTc6A2k5itUHfe-5iqkHvByfCpN79X7rBYfALfPkTtcCjHVlBu8p3wqV0HJq00tkXahEIOrhMJ752I0iFb9svjRG2upL2jw9WK97k6A90NE1ft9hAK5IgeoKpWq-sNKg2-09So8RgH3rG7lJTR9CnPUpia2PmVyZKDFiKasMmKLftNyTJ_OZt84J2gaDFFZuPN9QitFhWdNIMq8vGKMO8sX7ZPS4Gk2IFLUYnp5As0jmtKxQWy0E2hl6CVI1KcJJWip-ukH4XUkE9e013yEXTHVZj64a3-DvkBh3Oy5vgHxsm9B4BWmz_v_3fTSLXcbVze5-PJr4X5hskS--PkHmgFSlHV1rm1R__Ed7QExlQu_GgIRa79YoAtcx0RJHNaHDpLWzzryhOiuHtj_joiqSRsds-V9p-X1_1xQzrbVmSkHBGg26YE2I_d3LbM-G_UxrravLckVhMMQYq7kdjCRvZ4gj3W-nmEQLdP9yE1XgdEygWFhl8YXnSkfKdj1zwPEpftFOP9g5g0wuUvDqW1R05-6WCuZsrA-NG6AMcEcwNSW=w693-h179-no" title="" align="" />

### Ещё пример

Результат работы более сложного вызова сниппета с выводом превьюшек, даты и заголовка может выглядеть примерно так:
![siblings_demo_1](https://user-images.githubusercontent.com/6253807/50377091-b58ff300-0649-11e9-8880-f2672927e4af.png)

Подробнее о сниппете DLSiblings читайте на моем сайте: <a href="https://aharito.ru/modx-evolution/dlsiblings-podnimaem-sajt-po-nch-zaprosam">Сниппет DLSiblings</a>
