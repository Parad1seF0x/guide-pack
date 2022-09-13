# Подготовка страницы 

И так, нам нужно подготовить html страницу к вставке в наш "Эмулятор". Изначально мы имеем **только 1 файл**, нам нужно его **разбить на две составляющие**

Подготовим 2 файла - **имя.component.css** и **имя.component.html**, где *имя - назвние раздела* на англ.


# HTML

Нам необходимо внести некоторые изменения в html файле для корректной работы.
Сам HTML код, который мы берём из файла начинается на `<div id=app class=container>` и заканчивается на `<div id=h5playerContainer ...>`.  Весь этот код нужно отформатировать(*Любым удобным инструментом*) и вставить внутрь шаблона снизу

## \<html\> и \<body\>

Так как данные теги уже используются на самой странице, нам нужно их заменить на div-ы, которые будут принимать на себя стили, которые предназначались для **\<html\> и \<body\>**.

Таким образом у нас появляется начальный шаблон для каждого **html** файла:

```html
<div class="html" style="background-color: rgb(76, 75, 87);">
    <div class="body" style="background-color: rgb(76, 75, 87); position: static; overflow: visible;">
    	
    </div>
</div>
```


## Закрытие тегов

Проблема которая встречается в основном на страницах, на которых присутствуют **таблицы**. Дело в том что китайцы ~~пидоры~~ очень экономили на html коде из-за объёма памяти и в таблицах попросту **нету закрывающих тегов**. Нам эту ситуацию необходимо поправить. Выглядит это примерно так:

```html
<table class=el-table__header style=width:1374px cellspacing=0 cellpadding=0 border=0>  
	    <colgroup>  
		    <col name=el-table_1_column_33 width=100>  
		    <col name=el-table_1_column_34 width=200>  
		    <col name=el-table_1_column_35 width=265>  
		    <col name=el-table_1_column_36 width=264>  
		    <col name=el-table_1_column_37 width=264>  
		    <col name=el-table_1_column_38 width=264>  
		    <col name=gutter width=17>  
	    <thead>  
		    <tr>  
			    <th colspan=1 rowspan=1 class="el-table_1_column_33 is-center is-leaf">  
				    <div class=cell>№</div>  
			    <th colspan=1 rowspan=1 class="el-table_1_column_34 is-center is-leaf">
```
>В данном примере отсутствуют следующие теги `</table>`, `</colgroup>`, `</col>`, `</thead>`, `</tr>` и `</th>`

# CSS
По css изменения просты и сложного ничего нет.
Опять же форматируем код для удобного чтения и далее нас интересует код начиная с `:root{--sf-img-` и заканчивая `sf-hidden{display:none!important}` перед `</style><link rel=canonical`

## :root и замена классов

В css первым делом мы заменяем `:root` на `.html`
А дальше во всём css файле мы заменяем `html` на `.html` и `body` на `.body`
Всё это нужно для того чтоб наши классы стилей накладывались именно на div-ы из нашего шаблона сверху, а не на теги `html` и `body`

## Исправление графических ошибок.
Так же есть некоторые графические ошибки которые небоходимо исправить
1) Исправляем навбар:
ищем это
```css
.navbar { 
    background-color: #1f1f23; 
	height: 52px; 
	border-bottom: 1px solid #242330; 
	position: fixed; 
	width: 100%; 
	z-index: 1000 
}
```
Заменяем на это
```css
.navbar {
	background-color: #1f1f23;
	height: 52px;
	border-bottom: 1px solid #242330;
	position: relative;
	width: 100%;
	z-index: 1000
}
```
2) Исправляем отступ сверху:
ищем это
```css
.fn-mart30 {
	margin-top: 30px
}
```
Заменяем на это
```css
.fn-mart30 {
	margin-top: 0px
}
```

---
---
Пример вы можете видеть в той же папке, в которой лежит данная инструкция, тобишь [тут](https://github.com/Parad1seF0x/guide-pack/tree/main/web)