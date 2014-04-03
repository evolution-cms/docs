###Сниппет для формирования фильтра каталога на базе дерева документов.

Версия: 0.1

####Пример использования
*[!evoFilter? &parent=`[*id*]` &template=`5` &type=`ids`!]*
вернет список ID сформированный результатами фильтра, если не применялся фильтр то возвражает пустой результат
	
*[!evoFilter? &parent=`[*id*]` &template=`5` &type=`filters`!]*
Сформирует фильтра на основе настроек в тв параметре каталога: evoFilter на базе станадртных шаблон

####Необходимые доп решения для работы с evoFilter
- Сниппет multiTV 
- Скрипт jSlider
- js Библиотека bforms(идет в комплекте с evoFilter)
 
####Параметры сниппета

Параметр|Описание|Возможные значения|По-умолчанию
--------|--------|------------------|------------
parent|||
template|||
type|||
filters|||
outerTpl|||
checkboxOuterTpl|||
checkboxItemTpl|||
selectOuterTpl|||
selectItemTpl|||
storeOuterTpl|||
storeItemTpl|||
priceOuterTpl|||
priceItemTpl|||

####Типы фильтров
- **Цена** - слайдер с минимальным и максимальным значением (используется скрипт jSlider)
- **Наличие** - используется когда нужно проверить есть ли в наличии без учета количества
- **Чекбоксы** - список параметров с возможностью выбрать несколько работает по логике ИЛИ 
- **Селект** - спосок параметров когда возмонжо выбрать только 1 вариант

####Конфиг(multiTV) нужен для управления фильтрами  
	$settings['display'] = 'horizontal';
	$settings['fields'] = array(
		'title' => array(
			'caption' => 'Название',
			'type' => 'text',
			'width' => '200'
		),
		'name' => array(
			'caption' => 'Параметр фильтра',
			'type' => 'dropdown',
			'elements' => '@SELECT name FROM [+PREFIX+]site_tmplvars WHERE `category` IN(20,13) ORDER BY name ASC',
			'width' => '200'
	),
		'type' => array(
			'caption' => 'Тип фильтра',
			'type' => 'dropdown',
			'elements' => 'Цена==price||Наличие==store||Чекбоксы==checkbox||Селект==select',
			'width' => '200'
		)
	);
	$settings['configuration'] = array(
		'enablePaste' => FALSE,
		'enableClear' => FALSE,
		'csvseparator' => ','
	);
	
тут стоит обратить внимание на строку: 
	
	'elements' => '@SELECT name FROM [+PREFIX+]site_tmplvars WHERE `category` IN(20,13) ORDER BY name ASC',
	
В ней генерируется список тв параметров доступных для фильтрации

#### Картинки
http://monosnap.com/image/ay5pCXojPGL1cs0yQrLbHLwNvQYSGM
http://monosnap.com/image/JibuQ71aiDYebnGZwCNdRolVSQf2KQ


	
