[![AlexGyver YouTube](http://alexgyver.ru/git_banner.jpg)](https://www.youtube.com/channel/UCgtAOyEQdAyjvm9ATCi_Aig?sub_confirmation=1)
# Крутейший световой меч на Arduino своими рукамаи
* [Описание проекта](#chapter-0)
* [Папки проекта](#chapter-1)
* [Схемы подключения](#chapter-2)
* [Материалы и компоненты](#chapter-3)
* [Как скачать и прошить](#chapter-4)
* [FAQ](#chapter-5)
* [Полезная информация](#chapter-6)

<a id="chapter-0"></a>
## Описание проекта
Многоцветный световой меч на адресных светодиодах с воспроизведением звуков
#### ВОЗМОЖНОСТИ:
* Плавное включение/выключение со звуками меча
* Во время работы меч "пульсирует" случайным образом
* Во время работы издаёт звуки:
  + РЕЖИМ 1: тон "гудения" зависит от угловой скорости (гироскоп) поворота меча, т.е. взмаха
  + РЕЖИМ 2: гудение и звуки взмахов воспроизводятся с карты памяти
    - Медленный взмах - длинный звук взмаха (случайно один из 4)
    - Быстрый взмах - короткий звук взмаха (случайно один из 5)
* При ударе меч вспыхивает ярко-белым
* При ударе воспроизводится один из 16 звуков удара (случайно)
  + Слабый удар - короткие звуки
  + Сильный удар - длинные звуки
* При включении показывает уровень заряда аккумулятора длиной светящейся части в процентах
* Следит за напряжением аккумулятора:
  + Аккумулятор разрядился ДО ВКЛЮЧЕНИЯ: меч не включится, светодиод кнопки мигнёт несколько раз
  + Аккумулятор разрядился ВО ВРЕМЯ РАБОТЫ: меч выключается
#### УПРАВЛЕНИЕ:
* Включение/выключение по удерживанию кнопки
* Тройное нажатие - смена цвета (красный - зелёный - синий - жёлтый - розовый - голубой)
* Пятерное нажатие - смена звукового режима (режим генерации и режим звуков с карты памяти)
* Выбранный цвет и режим хранится в памяти и не сбрасывается при перезагрузке  

Подробности в видео: 

<a id="chapter-1"></a>
## Папки
**ВНИМАНИЕ! Если это твой первый опыт работы с Arduino, читай [инструкцию](#chapter-4)**
- **libraries** - библиотеки проекта. Заменить имеющиеся версии
- **GyverSaber** - прошивка для Arduino
- **schemes** - схемы подключения
- **SDsounds** - набор звуков для карты памяти

<a id="chapter-2"></a>
## Схемы
![SCHEME](https://github.com/AlexGyver/GyverSaber/blob/master/schemes/scheme1.jpg)
![SCHEME](https://github.com/AlexGyver/GyverSaber/blob/master/schemes/scheme2.jpg)

<a id="chapter-3"></a>
## Материалы и компоненты
* Arduino NANO http://ali.pub/20o35g  http://ali.pub/20o36t
* Адресная лента. Чип WS2811, напряжение 12 Вольт. Берём 2 метра ленты, на **белой подложке, без защиты от влаги, 60 светодиодов на метр**
http://ali.pub/23csyd  http://ali.pub/23cszc  http://ali.pub/23cszq
* Кнопочки с подсветкой. **Берём версию 5 Вольт** http://ali.pub/23ct29

## Вам скорее всего пригодится
* [Всё для пайки (паяльники и примочки)](http://alexgyver.ru/all-for-soldering/)
* [Недорогие инструменты](http://alexgyver.ru/my_instruments/)
* [Все существующие модули и сенсоры Arduino](http://alexgyver.ru/arduino_shop/)
* [Электронные компоненты](http://alexgyver.ru/electronics/)
* [Аккумуляторы и зарядные модули](http://alexgyver.ru/18650/)

<a id="chapter-4"></a>
## Как скачать и прошить
* [Первые шаги с Arduino](http://alexgyver.ru/arduino-first/) - ультра подробная статья по началу работы с Ардуино, ознакомиться первым делом!
* Скачать архив с проектом
> На главной странице проекта (где ты читаешь этот текст) вверху справа зелёная кнопка **Clone or download**, вот её жми, там будет **Download ZIP**
* Установить библиотеки в  
`C:\Program Files (x86)\Arduino\libraries\` (Windows x64)  
`C:\Program Files\Arduino\libraries\` (Windows x86)
* Подключить Ардуино к компьютеру
* Запустить файл прошивки (который имеет расширение .ino)
* Настроить IDE (COM порт, модель Arduino, как в статье выше)
* Настроить что нужно по проекту
* Нажать загрузить
* Пользоваться  

## Настройки меча
    NUM_LEDS 30         // число МИКРОСХЕМ на ленте
    BTN_TIMEOUT 800     // задержка кнопки для удерживания (миллисекунды)
    BRIGHTNESS 255      // максимальная яркость ленты (0 - 255)

    SWING_TIMEOUT 500   // таймаут между двумя взмахами
    SWING_L_THR 150     // порог угловой скорости для взмаха
    SWING_THR 300       // порог угловой скорости для сильного взмаха
    STRIKE_THR 150      // порог ускорения для распознавания удара
    STRIKE_S_THR 320    // порог ускорения для распознавания сильного удара
    FLASH_DELAY 80      // время вспышки при ударе (миллисекунды)

    BLINK_ALLOW 1       // разрешить мерцание
    BLINK_AMPL 20       // амплитуда мерцания клинка
    BLINK_DELAY 30      // задержка между мерцаниями

    R1 100000           // сопротивление резистора делителя    
    R2 51000            // сопротивление резистора делителя
    BATTERY_SAFE 1      // не включаться и выключаться при низком заряде АКБ

    DEBUG 0             // вывод в порт отладочной информации


<a id="chapter-5"></a>
## FAQ
### Основные вопросы
В: Как скачать с этого грёбаного сайта?  
О: На главной странице проекта (где ты читаешь этот текст) вверху справа зелёная кнопка **Clone or download**, вот её жми, там будет **Download ZIP**

В: Скачался какой то файл .zip, куда его теперь?  
О: Это архив. Можно открыть стандартными средствами Windows, но думаю у всех на компьютере установлен WinRAR, архив нужно правой кнопкой и извлечь.

В: Я совсем новичок! Что мне делать с Ардуиной, где взять все программы?  
О: Читай и смотри видос http://alexgyver.ru/arduino-first/

В: Компьютер никак не реагирует на подключение Ардуины!  
О: Возможно у тебя зарядный USB кабель, а нужен именно data-кабель, по которому можно данные передавать

В: Ошибка! Скетч не компилируется!  
О: Путь к скетчу не должен содержать кириллицу. Положи его в корень диска.

В: Сколько стоит?  
О: Ничего не продаю.

### Вопросы по этому проекту

<a id="chapter-6"></a>
## Полезная информация
* [Мой сайт](http://alexgyver.ru/)
* [Основной YouTube канал](https://www.youtube.com/channel/UCgtAOyEQdAyjvm9ATCi_Aig?sub_confirmation=1)
* [YouTube канал про Arduino](https://www.youtube.com/channel/UC4axiS76D784-ofoTdo5zOA?sub_confirmation=1)
* [Мои видеоуроки по пайке](https://www.youtube.com/playlist?list=PLOT_HeyBraBuMIwfSYu7kCKXxQGsUKcqR)
* [Мои видеоуроки по Arduino](http://alexgyver.ru/arduino_lessons/)