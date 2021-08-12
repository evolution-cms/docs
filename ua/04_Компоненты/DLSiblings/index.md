
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLSiblings: Висновок сусідніх ресурсів з шаблонізаціі </h2>

Висновок сусідніх ресурсів з шаблонізаціі (множинна кільцева перелинковка).

<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Aharito/DLSiblings" rel="nofollow" target="_blank">Aharito</a></p>

<strong>DLSiblings</strong> — сніпет виведення сусідніх ресурсів для Evolution CMS (MODx Evo). Призначений для організації множинної кільцевої перелинковки сторінок сайту. Заснований на сніпеті <strong>DocLister</strong>, тому можна використовувати всі можливості ДокЛістера.

<h3>Трохи теорії</h3>
Що таке множинна кільцева перелинковка? Сеошники напевно знають про неї. А для тих, хто не знає - це схема перелинковки сторінок сайту, що дозволяє непогано підняти сайт по низькочастотних і СНЧ запитам.

<em>*** Детальніше про кільцевої перелинковке читайте в моїй статті: <a href="https://aharito.ru/seo-prodvizhenie/shema-perelinkovki-stranic-sajta-pod-nch">Схема перелинковки сайту під НЧ</a></em>

<h3>Параметри сніпета</h3>
<ul>
<li><strong>&renderSnippet</strong> ( DocLister | sgController ) сніпет, який використовується для виведення, default DocLister</li>
    <li><strong>&prevQty</strong> - Кількість виведених сусідів-попередників, default 2</li>
    <li><strong>&nextQty</strong> - Кількість виведених сусідів-послідовників, default 2</li>
    <li><strong>все</strong> інші параметри і шаблони як в DocLister</li>
</ul>

Можна використовувати успадковані від DocLister (такі ж, як у нього): умови вибірки & addWhereList і & filters, умови сортування & orderBy, глибину вибірки & depth, prepare-сніпети і багато інших параметрів і всі шаблони.

Якщо в якості сніпета виведення вказано sgController, то відповідно можна використовувати і всі умови, параметри і шаблони sgController.

<h3>Шаблони сніпета</h3>
Всі шаблони - точно такі ж, як у DocLister. Плейсхолдери в шаблонах - теж точно такі ж, як в DocLister. Якщо в якості сніпета виведення вказано sgController, то шаблони і плейсхолдери - точно такі ж, як в sgController.

<h3>Установка</h3>
<ul>
    <li>Сніпет знаходиться <a href="https://github.com/Aharito/DLSiblings">на Github</a></li>
    <li>Архів потрібно <a href="https://github.com/Aharito/DLSiblings/archive/master.zip">скачать</a> і встановити через Extras ("Установка з архіву").</li>
</ul>

<h3>приклад</h3>

	[[DLSiblings?
		&idType=`parents`
		&parents=`[*parent*]`
		&tpl=`@CODE: <a href="[+url+]">[+tv.h1+]</a><br>`
		&prevQty=`2`
		&nextQty=`2`
		&tvList=`h1`
	]]



<em>*** Більше прикладів з кодом і поясненнями в моїй статті: <a href="https://aharito.ru/modx-evolution/dlsiblings-primery-perelinkovki">Приклади застосування DLSiblings</a></em>

<h3>Результат праці</h3>
У цьому прикладі параметром & parents ми задаємо вибірку, в якій будемо шукати сусідів - всі документи, що знаходяться в тій же папці, що і поточний.

Результатом роботи буде список посилань на статті, сусідні по ВД для поточної.

<img src="https://lh3.googleusercontent.com/0NDlBaOvEdAXJ8TYEn5JPDRlAYYK4Q3xBA6hzDAdABVXlQAPHwEaSTfxYOgj81HOQXPfrhbQGuE7ihiLpmrr_ew4wGnG_8NTl0OkyS6F-h9tGxTc6A2k5itUHfe-5iqkHvByfCpN79X7rBYfALfPkTtcCjHVlBu8p3wqV0HJq00tkXahEIOrhMJ752I0iFb9svjRG2upL2jw9WK97k6A90NE1ft9hAK5IgeoKpWq-sNKg2-09So8RgH3rG7lJTR9CnPUpia2PmVyZKDFiKasMmKLftNyTJ_OZt84J2gaDFFZuPN9QitFhWdNIMq8vGKMO8sX7ZPS4Gk2IFLUYnp5As0jmtKxQWy0E2hl6CVI1KcJJWip-ukH4XUkE9e013yEXTHVZj64a3-DvkBh3Oy5vgHxsm9B4BWmz_v_3fTSLXcbVze5-PJr4X5hskS--PkHmgFSlHV1rm1R__Ed7QExlQu_GgIRa79YoAtcx0RJHNaHDpLWzzryhOiuHtj_joiqSRsds-V9p-X1_1xQzrbVmSkHBGg26YE2I_d3LbM-G_UxrravLckVhMMQYq7kdjCRvZ4gj3W-nmEQLdP9yE1XgdEygWFhl8YXnSkfKdj1zwPEpftFOP9g5g0wuUvDqW1R05-6WCuZsrA-NG6AMcEcwNSW=w693-h179-no" title="" align="" />

### Ще приклад

Результат роботи складнішого виклику сніпета з висновком превьюшек, дати і заголовка може виглядати приблизно так:
![siblings_demo_1](https://user-images.githubusercontent.com/6253807/50377091-b58ff300-0649-11e9-8880-f2672927e4af.png)

Детальніше про сніпеті DLSiblings читайте на моєму сайті: <a href="https://aharito.ru/modx-evolution/dlsiblings-podnimaem-sajt-po-nch-zaprosam">Сніпет DLSiblings</a>
