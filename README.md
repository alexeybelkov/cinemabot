Ник бота: @lbelkov_bot  (сейчас отключен)     
Использовал aiohttp, aiogram, sqlite3, в качестве апи для запросов к базе фильмов IMDb использовал https://imdb-api.com/    
База данных - простенькая бд на sqlite3, почти как в simple_selects     
Ссылки для просмотра фильмов выдавал через Programmable Search Engine от Google     
Бота запустил на рабочем сервере.      
Команды (это вывод **/help**):     
To find a film you just need to send me it name      
**/start** for start or restart the bot      
**/help** for showing help      
**/stat** for showing your searching stats      
**/history** for search history, top down from old to new      
**/language** allow user to switch between two search languages russian (ru) and english (en). Current is en. Language choice will affect content of additional information about films     
Для упрощения взаимодействия добавил меню ![img.png](img.png)

Бот умеет обрабатывать случаи, когда введена неправильная команда (например **/statis** вместо **/stat**)        
Так же бот умеет обрабатывать случаи, когда не удалось получить ответ при поиске фильма (т.е. когда response.status != 200) или когда информации о фильме не оказалось в базе IMDB (например если ввести какую-нибудь абракадабру типа jsdhfkshdfjksdkfhskdjhf)

В некотором смысле бот поддерживает и русский (ru) и английский языки (en). Для переключения между языками используется **/language**    
При успешной выдаче результата о фильме, будет доступно 3 inline-кнопки:    
![img_1.png](img_1.png)
1) More info (показывает дополнительную информацию о фильме, только здесь можно увидеть влияние языка бота, при **/language** = ru, он покажет более подробное описание сюжета на русском языке а так же некоторые другие поля будут на русском)
2) Watch on "some website"
3) Watch on "some websiet"      
2 и 3 - ссылки на сайт где можно посмотреть фильмы

Для подачи информации в эти кнопки было использовано нечто вроде LRU кэша, т.е. если много пользователей запрашивают more info, то со временем давно запрошенная информация станет недоступна (удалится из RAM) 
