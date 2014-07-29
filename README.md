codestyle
=========

##Документация:
[стиль кодирования на js](js.md)
[по документированию](https://github.com/senchalabs/jsduck/wiki)

##Внешние ссылки:


[автоматическое кодревью jscs](https://github.com/mdevils/node-jscs)
установка

    npm install jscs -g

[готовый config для CTI](https://raw.githubusercontent.com/pavelpower/node-jscs/master/presets/cti.json)
добавить конфиг в глобальную библиотеку (linux):

    cd /usr/local/lib/node_modules/jscs/presets && sudo wget https://github.com/pavelpower/node-jscs/blob/master/presets/cti.json

[jsDoc плагин для jscs](https://github.com/zxqfox/jscs-jsdoc)
установка: 

    npm -g install jscs-jsdoc

##Конфиг для codereview в RubyMine

[CTI.xml](https://github.com/pavelpower/codestyle/blob/master/CTI.xml)

   $ cd .RubyMine60/config/codestyle
   $ wget https://raw.githubusercontent.com/pavelpower/codestyle/master/CTI.xml

###CSS

Для CSS так же используем инструментарий стилистики от разработчиков Yndex:

[CSSCumb](https://github.com/csscomb/csscomb.js)

он структуризирует css
