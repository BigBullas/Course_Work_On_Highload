#  Pinterest
### Course Work On Highload

## 1. Тема и целевая аудитория
**Pinterest** - фотохостинг, позволяющий пользователям добавлять в режиме онлайн изображения, помещать их в тематические коллекции и делиться ими с другими пользователями

### MVP

- Регистрация/авторизация
- Просмотр пинов
- Комментирование пинов
- Добавление реакции на пин
- Создание пинов
- Создание собственных досок и сохранение в них пинов

### Целевая аудитория
MAU составляет 450M/ Весь мир

#### Лучшие страны мира по количеству пользователей Pinterest по состоянию на 2023 год

| **Страна** | **Количество, млн** |
|------------|---------------------|
| USA        | 84.6                |
| Brazil     | 28.05               |
| Mexico     | 19.45               |
| Germany    | 15.88               |
| France     | 10.65               |
| Canada     | 8.44                |

Что касается целевой аудитории:
- 55% пользователей составляют люди в возрасте от 18 до 34 лет;
- Количество пользователей от 35 до 54 лет — 31%, а 55 лет и старше — 12%;
- Около 70% всех пользователей — женского пола, мужчины используют социальную сеть намного реже (24%);

### Источники:
- https://www.demandsage.com/pinterest-statistics/
- https://tengyart.ru/statistika-pinterest-v-2020-informacziya-o-auditorii/?ysclid=lmf3csx7nl463560350

## 2. Расчёт нагрузки

### Продуктовые метрики

- Месячная аудитория 450 млн
- Дневная аудитория 225 млн
- Средний размер хранилища пользователя:  
  
Так как Pinterest не предоставляет никакой информации о количестве пинов у одного пользователя,
то возьмём, что в среднем у одного пользователя их 50 штук.  
Пины это файлы в формате .jpg или .mp4, то есть видео и изображения.  
Максимальный размер последних Pinterest установил 20 Mb, то есть будем считать, что в среднем изображение будет весить 10 Mb.  
Видео же должны быть размером меньше 100 Mb, то есть в среднем будут весить 50 Mb.  
На основе информации с данного сайта https://buffer.com/resources/pinterest-marketing-study/ видно, что 99% пинов
это изображения и всего лишь 1% видео.  
Тогда средний размер хранилища пользователя:

```azure
49 * 10 Mb + 1 * 50 Mb = 540 Mb
```

- Среднее количество действий пользователей по типам в день:  
  
С 2022 по 2023 года аудитория Pinterest возросла на 17 млн, то есть в день в среднем регистрировались 46,6 тысяч раз.
Авторизацию же проходят в среднем 4 раза в год, поэтому в день авторизацию проходят в среднем примерно 2,5 млн раз.  
Если взять в расчёт, что один пользователь в среднем смотрит около 50 пинов, то выходит, что в день просматривают
пины около 11 млрд раз.  
Один пользователь комментируют обычно 3 пина в день, тогда комментируют в день 675 млн раз в целом.  
Реакции ставят чаще, около 10 в день, следовательно их добавляют на пины в день около 2 млрд раз.  
Что касается создания пинов, то рядовой пользователь делает это крайне редко,
этим чаще всего занимаются различные юридические лица. Поэтому будем считать, что в день это совершается всего 0,5 раз, 
отсюда получаем, что в день создают пины 112,5 млн раз.  
Создание досок у обычного пользователя происходит в среднем 1 раз в месяц, поэтому в целом 7,5 млн раз.
Что не скажешь о добавлении пинов, в среднем пользователь может сохранить около 5 пинов в день,
то есть в итоге получим около 1 млрд раз.  

| **Действие**          | **Среднее количество в день, штук** |
|-----------------------|-------------------------------------|
| Регистрация           | 46.6 тысяч                          |
| Авторизация           | 2.5 млн                             |
| Просмотр пинов        | 11 млрд                             |
| Комментирование пинов | 675 млн                             |
| Добавление реакции    | 2 млрд                              |
| Создание пина         | 112.5 млн                           |
| Создание досок        | 7.5 млн                             |
| Сохранение пинов      | 1 млрд                              |

### Технические метрики

#### Хранилище

- Регистрация  
  
Здесь основную часть будут занимать аватарки пользователей, средний вес которой равен 5 Мб
За всё время (2009 - 2023): 450 млн пользователей * 5 Мб = 2 146 Тб = 2 Пб  
За год: 2 146 Тб / 14 лет = 153 Тб  
За квартал: 38 Тб  

- Создание пина  
  
Судя по данному источнику
https://aliexpress.inform.click/10-statisticheskih-dannyh-pinterest-kotorye-dolzhen-znat-kazhdyj-marketolog-v-2021-godu-infografika/
в 2019 году у Pinterest было всего около 200 млрд пинов.  
Информацию о том, сколько пинов в среднем добавляет 1 пользователь нет, поэтому возьмём рекомендацию о том, что в среднем
стоит добавлять новых пинов от 1 до 5 пинов (в среднем 3 пина), из источника:
https://www.affde.com/ru/how-many-pinterest-pins-should-i-pin-per-day.html  
Из источника https://www.demandsage.com/pinterest-statistics/ видно, что активных пользователей с 2019 года по 2023 в среднем
было 450 млн, но учитывать будем именно дневную активную аудиторию 225 млн. Тогда с 2019 по 2023 новых пинов примерно появилось:

```azure
4 года * 365 дней * 3 пина * 225 000 000 пользователей = 985,5 млрд пинов
```  

То есть итого сейчас у Pinterest около 1,2 триллиона пинов.  
Как писалось выше, 99% из них это изображения. Отсюда:  
За всё время:  
- Изображения: 1.2 трлн * 0.99 * 10 Mb = 11 064 Пб = 10 Еб (10 эксабайт)
- Видео: 1.2 трлн * 0.01 * 50 Mb = 560 Пб (560 петабайт)
- Итого: 11 564 Пб  
  
За год: 826 Пб  
За квартал: 206.5 Пб  

- Создание комментария 
  
Максимальная длина комментария - 500 символов Unicode, то есть в среднем пусть длина комментария будет 250 символов.
Тогда 1 комментарий будет занимать 500 байт. В день комментируют 675 млн раз. Тогда:  
За квартал: 500 байт * 675 млн * 90 дней = 27 Тб  
За год: 110.5 Тб  
За всё время: 1547 Тб  

Из незначительных по объёму хранилища
- Создание досок: название доски может содержать 50 символов (взято из валидации инпут поля при создании доски),
то есть одна доска будет занимать в среднем 25 * 2 байта = 50 байт
- Добавление реакции на пин: хранить нужно счётчик, id пина, id самой реакции, id статичной картинки реакции
(8 байт + 16 байт + 16 байт + 16 байт = 56 байт)

| **Действие**          | **Объём памяти за всё время** | **Объём памяти за год** | **Объём памяти за квартал** |
|-----------------------|-------------------------------|-------------------------|-----------------------------|
| Регистрация           | 2 Пб                          | 153 Тб                  | 38 Тб                       |
| Комментирование пинов | 1 547 Тб                      | 110.5 Тб                | 27 Тб                       |
| Создание пина         | 11 564 Пб                     | 826 Пб                  | 206.5 Пб                    |

#### Сетевой трафик и rps

Сводная таблица RPS по типовым действиям, средний и пиковый трафики

| **Действие**          | **Тип** | **RPS**  | **RPD**    | **Средний трафик** | **Пиковый трафик** |
|-----------------------|---------|----------|------------|--------------------|--------------------|
| Регистрация           | Запись  | 0.54     | 46.6 тысяч | 2.7 Мб/с           | 4.59 Мб/с          |
| Авторизация           | Чтение  | 3 тыс    | 2.5 млн    | 146.5 Мб/с         | 249 Мб/с           |
| Просмотр пинов        | Чтение  | 127 тыс  | 11 млрд    | 1.2 Тб/с           | 2 Тб/с             |
| Комментирование пинов | Запись  | 8 тыс    | 675 млн    | 3.8 Мб/с           | 6.5 Мб/с           |
| Добавление реакции    | Запись  | 23 тыс   | 2 млрд     | 1.2 Мб/с           | 2.1 Мб/с           |
| Создание пина         | Запись  | 1 тыс    | 112.5 млн  | 9.8 Гб/с           | 16.6 Гб/с          |
| Создание досок        | Запись  | 86       | 7.5 млн    | 4.2 Кб/с           | 7.1 Кб/с           |
| Сохранение пинов      | Запись  | 11.6 тыс | 1 млрд     | 113 Гб/с           | 192.6 Гб/с         |

Пояснение для таблицы:
- RPD взято из пункта выше Среднее количество действий пользователей по типам в день
- RPS = RPD / 86400. Здесь 86400 = 24 часа * 60 минут * 60 секунд
- Средний трафик = RPS * <Вес сообщения из пункта выше Хранилище>
- Пиковый трафик = <Средний трафик> * <Коэффициент отношения пикового трафика к среднему = 2 (на основе данного источника: https://buffer.com/resources/pinterest-scheduling-frequency-timing/ )>  

## 3. Глобальная балансировка нагрузки

### Расположение датацентров

Из источника https://www.demandsage.com/pinterest-statistics/ ясно, что основные пользователи Pinterest находятся
в таких регионах, таких как Северная Америка, Южная Америка, Европа и Азия (а именно Япония).  
Поэтому датацентры Pinterest будут в: Сан-Франциско, Нью-Йорк (как одни из крупнейших городов США), Берлин (является ключевым городом в Европе), 
Индзай (находится неподалёку от Токио, крупнейшего города мира и технологического центра Японии), Сан-Паулу (крупнейший город в Бразилии и имеет крупнейшую экономику в регионе, а Бразилия находится на втором месте по количеству пользователей Pinterest).

### Глобальная балансировка

Балансировка нагрузки будет осуществляться следующим образом:  
**GeoDNS**: для определения местоположения клиента на основе его географических данных,
что позволяет направить его к наиболее близкому серверному центру в соответствующем регионе.  

**BGP Anycast**: для определения ближайшего серверного центра в данном регионе,
что обеспечивает эффективное распределение нагрузки.

## 4. Локальная балансировка нагрузки

### Схемы балансировки для входящих и меж сервисных запросов

Будем использовать L7-балансировку на NGINX на отдельных серверах, так как это позволит кэшировать статику
(которой будет немало) и динамику, есть SSL терминация (сертификаты SSL можно получить из Let's Encrypt),
присутствует сжатие GZIP (что также важно для Pinterest). Также за счёт L7-балансировки мы можем поделить сервисы по
обработке какого-либо конкретного функционала или же по категориям пинов (учитывая их огромное количество).

### Схема отказоустойчивости

У L7-балансировки присутствует пассивная проверка состояния серверов. Однако у NGINX есть минус в том, что ему долго
даются большие конфиги и при этом не поддерживает динамическое обновление конфигурации. Для этого можно использовать
Envoy, который способен читать большие измененные конфигурационные файлы без необходимости перезапуска.
Также следует верно настроить timeout для разных типов запросов, чтобы долго не ожидать статуса о том, что сервер не работает.

## 5. Логическая схема БД

Ссылка на [ER_диаграмму](https://drawsql.app/teams/bashkirs/diagrams/pinterest)

![](./resources/ER_diargamm.png)

## 6. Физическая схема БД

### Индексы

- Индекс по ID пользователя в таблице "Пользователи"  
CREATE INDEX idx_users_id ON Пользователи (ID);

- Индекс по ID пина в таблице "Пины"  
CREATE INDEX idx_pins_id ON Пины (ID);

- Индекс по заголовку пина в таблице "Пины"  
CREATE INDEX idx_pins_title ON Пины (Заголовок_пина);

- Индекс по ID пользователя в таблице "Пины"  
CREATE INDEX idx_pins_user_id ON Пины (ID_пользователя);

- Индекс по ID статистики в таблице "Пины"  
CREATE INDEX idx_pins_stats_id ON Пины (ID_статистики);

- Индекс по ID комментария в таблице "Комментарии"  
CREATE INDEX idx_comments_id ON Комментарии (ID_комментария);

- Индекс по ID пина в таблице "Комментарии"  
CREATE INDEX idx_comments_pin_id ON Комментарии (ID_пина);

- Индекс по ID реакции в таблице "Реакции на пины"  
CREATE INDEX idx_pin_reactions_id ON Реакции_на_пины (ID_реакции);

- Индекс по ID пина в таблице "Реакции на пины"  
CREATE INDEX idx_pin_reactions_pin_id ON Реакции_на_пины (ID_пина);

- Индекс по типу реакции в таблице "Реакции на пины"  
CREATE INDEX idx_pin_reactions_type ON Реакции_на_пины (Тип_реакции);

- Индекс по ID реакции в таблице "Реакции на комментарии"  
CREATE INDEX idx_comment_reactions_id ON Реакции_на_комментарии (ID_реакции);

- Индекс по типу реакции в таблице "Реакции на комментарии"  
CREATE INDEX idx_comment_reactions_type ON Реакции_на_комментарии (Тип_реакции);

- Индекс по ID комментария в таблице "Реакции на комментарии"  
CREATE INDEX idx_comment_reactions_comment_id ON Реакции_на_комментарии (ID_комментария);

- Индекс по ID категории в таблице "Категории"  
CREATE INDEX idx_categories_id ON Категории (ID_категории);

- Индекс по ID пина на доске в таблице "Пины на доске"  
CREATE INDEX idx_board_pins_id ON Пины_на_доске (ID_пина_на_доске);

- Индекс по ID доски в таблице "Пины на доске"  
CREATE INDEX idx_board_pins_board_id ON Пины_на_доске (ID_доски);

- Индекс по ID записи в таблице "Пины-Категории"  
CREATE INDEX idx_pin_categories_id ON Пины_Категории (ID_записи);

- Индекс по ID категории в таблице "Пины-Категории"  
CREATE INDEX idx_pin_categories_category_id ON Пины_Категории (ID_категории);

- Индекс по ID пина в таблице "Пины-Категории"  
CREATE INDEX idx_pin_categories_pin_id ON Пины_Категории (ID_пина);  

### Денормализация

Приведена на [ER-диаграмме](https://drawsql.app/teams/bashkirs/diagrams/copy-of-pinterest)

### Выбор СУБД (потаблично)

- ClickHouse (колоночная база данных, разработанная для обработки аналитических запросов) будем использовать для таблицы pin_statistics
- PostgreSQL (реляционная база данных) будем использовать для оставшихся таблиц
- Amazon S3 (служба хранения данных в облаке) будем использовать для хранения аттачей (изображение, видео) 

### Шардирование (потаблично)

 - Pins по pin_id
 - Users по user_id
 - Boards по user_id
 - Comments по pin_id
 - Reactions_to_pin по pin_id
 - Reactions_to_comment по pin_id
 - Board_pins по board_id
 - Pin_statistics по statistic_id

### Клиентские библиотеки / интеграции

Язык бэкенда - Go, отталкиваясь от этого были выбраны следующие коннекторы/библиотеки:
- pgx (https://github.com/jackc/pgx) - Go пакет, предоставляющий высокоуровневый доступ к базе данных PostgreSQL  
- go-clickhouse - коннектор для языка Go, который позволяет взаимодействовать с базой данных ClickHouse  
- AWS SDK (https://pkg.go.dev/github.com/aws/aws-sdk-go) - Software Development Kit (пакет разработки программного обеспечения), предоставляемый Amazon Web Services (AWS), который позволяет разработчикам взаимодействовать с Amazon S3  

## 8. Технологии
 
### Backend сервис
Реализовываться будет на языке Go. Его основные преимущества:
1. Производительность
2. Простота разработки
3. Масштабируемость
4. Надежность
5. Богатая стандартная библиотека
6. Большое коммьюнити
7. Простая параллельность: горутины и каналы, что облегчает разработку многопоточных программ.

Будет использована микросервисная архитектура на основе Бизнес-сервисов. Можно выделить следующие миркосервисы: сервис авторизации и регистрации, сервис управления пинами, сервис реакций и комментариев, сервис статистики.
Основные преимущества микросервисной архитектуры:
  - Ускорение разработки
  - Повышение надежности
  - Повышение гибкости
  - Повышение управляемости
Минусы:
 - Увеличение накладных расходов. Можем сократить их за счёт gRPC общения между микросервисами
 - Риск overengineering — для нашего небольшого MVP приложения это не так страшно

Почему именно на основе Бизнес-сервисов? Это логичное и понятное разделение сервиса, удобное для дальнейшего интегрирования новых микросервисов

### Frontend
Будет реализован на React, TypeScript. Основной конкурент React-а это Vue. Но он появился позже, а также нет специальной платформы для создания мобильных приложений. В отличие от React, у него есть платформа React Native, которая хорошо интегрируется с React-ом. TypeScript же нужен для строгой типизации, что позволяет отсечь быстрее часть ошибок во время разработки.

### Балансировщик
Будет использоваться NGINX, так как это позволит кэшировать статику (которой будет немало) и динамику, есть SSL терминация (сертификаты SSL можно получить из Let's Encrypt),
присутствует сжатие GZIP (что также важно для Pinterest). Его основной конкурент это Envoy.
Был взят Nginx, так как это один из наиболее популярных серверов web-прокси с более чем 20-летней историей с большим сообществом и опытом использования в продакшн средах.

### Оркестратор
На данный момент в нём нет никакой необходимости, однако в будущем, с ростом сервиса и бизнес-задач оркестратор можно будет интегрировать для более удобного взаимодействия между микросервисами

### Брокер сообщений
Можно будет использовать его для записи пинов в Amazon S3, а также для записи статистики по количеству просмотров пинов, их сохранений, количества реакций, комментариев.
Для данных функций можем использовать Kafka. Взял его, так как RabbitMQ и Celery имеют недостаточную производительность для больших нагрузок. В данном случае Kafka новее, более производительнее, имеет больше возможностей.

