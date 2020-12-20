# Вбудовані модифікатори

Є вбудованою заміною плагіна PHx.
Вмикаються параметром `enable_filter` в загальних налаштуваннях сайта.

## Переваги

+ Легкі в порівнянні з PHx
+ Можна використовувати в чанках і снипетах
+ Гнучкість
+ Легко читатити
+ Не залежать від розділювачів: ( ' " `
+ Багато варіантів модификаторів
+ Сумісні з плагіном PHx
+ Можут використовуватись одночасно з плагіном PHx
	
## Приклади:

Приклад 1: варіанти оформлення

```
[*longtitle:ifempty=[*pagetitle*]*]
[*longtitle:ifempty='[*pagetitle*]'*]
[*longtitle:ifempty="[*pagetitle*]"*]
[*longtitle:ifempty([*pagetitle*])*]
[*longtitle:ifempty('[*pagetitle*]')*]
```

Пример 2: регістронезалежність

```
[*template:is(1):then(Top page):else(Sub page)*]
[*template:IS(1):THEN('Top page'):ELSE('Sub page')*]
```

Пример 3: оформлення в декількох рядках

```
[*id
:is(1)
:then(Top)
:else(Other)
*]
```

Ще приклади:

```
[*email:spam_protect*]
[*price:number_format*]
[*content:addBreak*]
[*pagetitle:strip_tags*]
[(site_name:escape)]
{{Chunk:escape}}
[+placeholder:escape+]
[[Snippet:escape?param=1&param2]]
[!$_SERVER['REQUEST_TIME']:dateFormat('Y-m-d H:i:s')!]
[*pict:is_image:tpl('<img src="[+value+]" alt="">')*]
[+image:isNotEmpty
  :then('<img src="[[phpthumb? &input=`[+image+]` &options=`w=300`]]" alt="">')
  :else('[+wf.linktext:substr(0,1)+]')
  +]
[*pub_date:ifEmpty('[*publishedon*]'):dateformat=`%d.%m.%Y`*]
```
