<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>OpenGraphTags: Виведення OG-тегів для статті </h3>
Сніпет виведення OG-тегів для статті у Evolution CMS.
<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Aharito/OpenGraphTags/blob/master/snippet.OpenGraphTags .php" rel="nofollow" target="_blank">Aharito</a></p>
<h3 class="sub-header">Параметри:</h3>
<h3 class="sub-header text-bold">tplList</h3>
<p>список шаблонів через кому, <span class="text-warning">ОБОВ'ЯЗКОВИЙ!!</span></p>
<h3 class="sub-header text-bold">locale</h3>
<p>string за замовчуванням "ru_RU"</p>
<h3 class="sub-header text-bold">site_name</h3>
<p>string за замовчуванням [(site_name)]</p>
<h3 class="sub-header text-bold">flag</h3>
<p>string, ім'я ТВ-параметра-прапора (чекбокс, ним можна увімкнути/вимкнути виведення OG-тегів для статті, навіть якщо її шаблон у списку $tplList). За замовчуванням 1 (увімкнено).</p>
<h3 class="sub-header text-bold">thumbSnippet</h3>
<p>string - сніппет для превьюшек як у SG та FastImage. Наприклад, "sgThumb" або "phpthumb". За промовчанням пусто.</p>
<h3 class="sub-header text-bold">thumbOptions</h3>
<p>string - опції превьюшки, задані як у SG або FastImageTV або phpthumb. За промовчанням пусто.</p>
<p><span class="text-primary">NOTE:</span> Для роботи сніпета повинні бути створені наступні ТВ-параметри:</p>
<ul>
<li><span class="text-danger">og_on_off</span> - ТВ-параметр-прапор (чекбокс, ним можна включити/відключити виведення OG-тегів для статті, навіть якщо її шаблон є у списку $tplList)< /li>
<li><span class="text-danger">og_title</span> - заголовок для соцмереж, якщо не заданий, соцмережі найчастіше беруть Title.</li>
<li><span class="text-danger">og_description</span> - опис для соцмереж, не більше 137 символів за моїми експериментами</li>
<li><span class="text-danger">og_image</span> - картинка для соцмереж, якщо не задана, соцмережі шукають картинки в контенті</li>
</ul>

<h3 class="sub-header">Приклад виклику сніппета:</h2>
<pre class="brush: html;">
[[OpenGraphTags? &tplList=`31,32` &site_name=`[(cfg_company_brand_name)]` &thumbSnippet=`sgThumb` &thumbOptions=`840x420`]]
</pre>

<h3 class="sub-header">Код сніпету:</h2>
<pre class="brush: php;">
&lt;?php
/**
 * OpenGraphTags
 * Виводить OG-теги лише для вказаних шаблонів.
 *
 * @category snippet
 * Це повинні бути тільки шаблони статей (og_type – жорстко прописаний як article)!!!
 * Виводить непусті значення тегів OpenGraph, зазначені в адмінці для посту
 *
 * @param $tplList - список шаблонів через кому, ОБОВ'ЯЗКОВИЙ!!
 * @param $locale, string, за замовчуванням "ru_RU"
 * @param $site_name, string, за замовчуванням [(site_name)]
 * @param $flag, string, ім'я ТВ-параметра-прапора (чекбокс, ним можна включити/вимкнути виведення OG-тегів для статті, навіть якщо її шаблон у списку $tplList). За замовчуванням 1 (увімк.).
 *
 * @param &thumbSnippet, string - сниппет для превьюшек як у SG та FastImage. Наприклад, "sgThumb" або "phpthumb". За промовчанням порожньо.
 * @param &thumbOptions, string - опції превьюшки, задані як у SG або FastImageTV або phpthumb. За промовчанням порожньо.
 *
 * @NOTE: Для роботи сніпету повинні бути створені наступні ТВ-параметри:
 * og_on_off - ТВ-параметр-прапор (чекбокс, ним можна включити/вимкнути висновок OG-тегів для статті, навіть якщо її шаблон є у списку $tplList)
 * og_title - заголовок для соцмереж, якщо не заданий, соцмережі найчастіше беруть Title.
 * og_description - опис для соцмереж, не більше 137 символів за моїми експериментами
 * og_image - картинка для соцмереж, якщо не задана, соцмережі шукають картинки в контенті
 *
 *
 * @internal @category SMO
 *
 * @version 0.2
 * @author Aharito http://aharito.ru
 *
 *
 * @example [[OpenGraphTags? &tplList=`31,32` &site_name=`[(cfg_company_brand_name)]` &thumbSnippet=`sgThumb` &thumbOptions=`840x420`]]
**/

$out = '';

$tplList = str_replace(" ", "", $tplList); //Прибираємо можливі зайві прогалини між ID шаблонів у списку
$_tplList = explode(",", $tplList);

$docObject = $modx->documentObject;

if ( in_array($docObject['template'], $_tplList) && $docObject['og_on_off'][1] ) { // Якщо шаблон у списку $tplList, і якщо прапор "увімкнено"

// Ці параметри задані один раз при викликі сніпету OpenGraphTags
$site_name = isset($site_name)? $site_name : $modx->getConfig('site_name');
$locale = isset($locale)? $locale: "ru_RU";

// Ці параметри задаються під час редагування кожної статті
// Якщо вони не задані, то для них 100% дефолтні значення, вони і виводяться
$title = !empty($docObject["og_title"][1]) ? $docObject["og_title"][1] : $docObject["pagetitle"];
$url = $modx->makeUrl($docObject["id"], '', '', 'full'); // Була нагода редагувати УРЛ, але я прибрав за непотрібністю

// Ці параметри задаються під час редагування кожної статті
// Для них немає 100% дефолтних значень, тому якщо вони не задані, то взагалі не виводимо відповідний метатег
$desc = !empty($docObject["og_description"][1]) ? $docObject["og_description"][1] : $modx->runSnippet('summary', array('text' => $docObject['content'], 'len' => '50'));
$descTPL = !empty($desc)? '&lt;meta property="og:description" content="' .$desc. '"&gt;' : '';

$imgTPL = !empty($docObject["og_image"][1]) ? '&lt;meta property="og:image" content="' .(isset($thumbSnippet) ? $modx->runSnippet($thumbSnippet, array("input" => $docObject["og_image"][1], "options"=>$thumbOptions)) : $docObject["og_image"][1]).'"&gt;' : '';

$out .= '<meta property="og:site_name" content="' . $site_name . '">';
$out .= PHP_EOL."\t".'<meta property="og:locale" content="' . $locale . '">';
$out .= PHP_EOL."\t".'<meta property="og:type" content="article">';
$out .= PHP_EOL."\t".'<meta property="og:title" content="' .$title. '">';
$out .=$descTPL? PHP_EOL."\t".$descTPL : '';
$out .=$imgTPL? PHP_EOL."\t".$imgTPL : '';
$out .= PHP_EOL."\t".'<meta property="og:url" content="' . $url . '">';
}

return $out;
</pre>