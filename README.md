# py-parser-examples
## Примеры для написания парсера сайта

* __Пример 1__. Парсер ТВ-программы с сайта yandex.ru

Содержит две программы (parser-01 и parser-02).  
* __parser-01__ - написан для старого варианта оформления сайта  
* __parser-02__ - написан для нового варианта оформления сайта  

Обе программы работают одинаково, отличается лишь только запрос `txt = requests.get(url, headers=head).text` к сайту - подробности смотрите ниже...  

---

Если кто-то пишет парсер на питоне по моим старым видео-урокам, то может столкнуться с одной проблемой...  
На сайте yandex.ru внели изменения, поэтому результаты parser-01 отличаются от видеоурока.  
Сайт определяет, что запрос идёт от программы-парсера, а не от браузера...  
Но можно представиться браузером и в запросе requests.get послать заголовок UserAgent, который можно узнать из вашего браузера из панели "Сеть" (пункт Headers) в "Инструментах разработчика" (по клавише F12).  
Этот вопрос обсуждается вот в этом [посте на хабре](https://habr.com/ru/post/280238/)  
Я у себя сделал это через два браузера в Windows:  
1) такой заголовок мне дал браузер FireFox -  
'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:70.0) Gecko/20100101 Firefox/70.0'  
2) такой заголовок мне дал браузер Chrome -  
'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.87 Safari/537.36'  
И через два браузера в Линуксе:
3) такой заголовок мне дал браузер FireFox -  
'User-Agent': 'Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:73.0) Gecko/20100101 Firefox/73.0'  
4) такой заголовок мне дал браузер Chrome -  
'User-Agent': 'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.122 Safari/537.36'  
Все эти заголовки позволяют нормально парсить сайт...  

---  

__ВНИМАНИЕ!__ Не забывайте, что вам нужно ещё сделать небольшой диалог пользователя:  
__шаг 1__ - пусть ваш парсер сначала выводит на экран названия ТВ-каналов, например:
1. СТС  
2. Культура  
3. Домашний  
4. ОТР  
5. НТВ  

__шаг 2__ - далее пользователь делает свой выбор, например вводит цифру 2 и в ответ ваш парсер формирует для пользователя ТВ-программу на сегодняшний день по телеканалу Культура, выводит в файл result.txt и в первой строке файла пусть напишет название канала (для удобства пользователя), а далее собственно строки с ТВ-программой, примерно так:
  
Культура  
04:55	Наедине со всеми  
06:00	Новости  
06:10	Уснувший пассажир  
07:40	Часовой. ОМОН на транспорте  
08:10	Здоровье. Выпуск от 10 ноября  
09:20	Непутевые заметки  
10:00	Новости  
...  

---  

[Регулярные выражения в Питоне](https://habr.com/ru/post/349860/)  

---  

