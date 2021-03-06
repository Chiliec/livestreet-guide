Создание заготовки LiveStreet-плагина
==========================
Плагин (от англ. plug-in) — независимо компилируемый программный модуль, динамически подключаемый к основной программе, предназначенный для расширения и/или использования её возможностей. Также может переводиться как «модуль». Плагины обычно выполняются в виде разделяемых библиотек. 

LiveStreet имеет встроенные средства для создания заготовки плагина, но о них мало кто знает. В Unix-подобных системах нужно лишь запустить при помощи `php` файл `путь_к_livestreet\engine\console\ls` с параметрами `plugin new название_плагина`. Запустив этот файл без параметров, вы получите краткую справку о командах. В общем разработчики, использующие такие системы скорее всего разберутся без проблем.

Гораздо сложнее разобраться с использованием консоли будет пользователям Windows, ведь консоль здесь используется не так часто и многие пользователи просто о ней не знают. Зато есть исполняемые bat-файлы, которые могут помочь автоматизировать использование консоли и сделать её комфортной. Итак, создаем новый файл с расширением .bat, записываем в него:
~~~
@echo off
set /p var="Введите имя плагина: "
C:\WebServers\usr\local\bin\php.exe C:\WebServers\home\su\livestreet\engine\console\ls plugin new "%var%"
Pause
~~~
Меняем пути на свои и сохраняем в кодировке DOS-866. Теперь не нужно прописывать все пути заново — достаточно запустить этот файл и ввести название нового плагина:

![Использование консоли для создания заготовки плагина](http://livestreet.ru/uploads/images/01/32/67/2012/08/14/e16e54.png "Использование консоли для создания заготовки плагина")

![Использование консоли для создания заготовки плагина](http://livestreet.ru/uploads/images/01/32/67/2012/08/14/3a8753.png "Использование консоли для создания заготовки плагина")

Структура плагина
-----------------
Плагин должен соответствовать заданным стандартам, и иметь два обязательных файла - `plugin.xml` и `Plugin<name>.class.php`.

* `plugin.xml` - это xml файл с информацией о плагине, его название, версия, автор, сайт автора и ссылка на страницу с настройками.
* `Plugin<name>.class.php` - файл необходимый для создания класса, для обращения к функциям плагина.

В плагине могут быть следующие каталоги:  
- classes  
-- actions  
-- hooks  
-- modules  
- config  
- include  
-- ajax  
-- lib  
- templates  
-- language  
-- skin  