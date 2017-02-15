Title: Emacs для не-восьминогів. Частина 1
Category: Emacs
Tags: emacs, ergoemacs, lisp, gnu, tutorial
Slug: emacs-for-non-octopus-p1
Image: /images/octopus.jpg
Date: 22/10/2016
Lang: uk
Summary: Чи справді Emacs був придуманий восьминогами?
          Як бути якщо в тебе немає щупалець?

## Зміст

[TOC]

## Короткий вступ

Мені давно хотілось якось об’єднати всі набуті знання про Emacs в збірник заміток, тому якщо лінь не
переможе, я напишу 2,3 ... n частину.

Зразу хотілось би сказати, що я не є спеціалістом, радше аматором, проте, на даний момент, в
інтернеті не так багато інформації на дану тематику, а тим паче українською. 

Це оглядовий пост, або швидке знайомтсво з редактором, більш детальні інструкції з налаштування та
редагування будуть згодом.


## Навіщо потрібен Emacs?

### 1. Прикладний редактор

Я використовую Emacs як прикладний редактор, тобто для тих речей для яких відкривати IDE просто не
доцільно, або людської IDE ще не написали.

Для ілюстрації уявімо сценарій: мені потрібно відредагувати конфіг NGINX
на [VDS](https://m.do.co/c/6463f665f8bc){rel=nofollow target=_blank} до якого я маю доступ через SSH.

1. `C-x C-f /:ssh:user@server:/path/to/file` --- відкриваю віддалений файл точно так само і локальний;
2. `M-x nginx-mode` --- вмикаю nginx-mode який дає підсвітку й автоматичне форматування файлу;
3. `C-x r m` --- додаю закладку і вказую ім'я файлу на свій смак.

Все, тепер я можу будь-який момент можу натиснути ``C-x r l` і обрати потрібну мені
закладку. Просто і зручно.

### 2. IDE для нових/рідкісних мов програмування чи розмітки

Редактор підтримує просто широченний спектр синтаксисів і їх діалектів (близько
127 [ref][EmacsWiki --- Programming Modes](https://goo.gl/bgQtQb){rel=nofollow target=_blank}[/ref]
штук не рахуючи сторонніх додатків), тим паче ви можете створити підтримку власного або комбінувати
декілька мов.

**Не варто порівнювати Emacs з IDE для популярних мов програмування, а особливо з продуктами від
JetBrains, це два різних класи інструментів.

## Переваги?

### 1. Гнучкість в налаштуванні

Ви можете змінити фактично все, що ви хочете: `M-x customize` телепортує вас у безкінечний світ
налаштування які стосуються не лише самого редактора, але і 90% додатків. Іноді це може зіграти з
вами злий жарт, тому варто користуватись "першою заповіддю радіотехніків" і не намагатись крутити
всі ручки одразу.

![Контрольна панель літака](images/plane-control-panel.jpg)
: В літаку теж багато тумблерів, але не варто натискати всі одразу.

### 2. Тонна додатків

Emacs має просто велетенську купу додатків за допомогою яких можна вирішити широкий спектр завдань.
Існує навіть окремий ресурс, на якому автор публікує огляд роботи з додатками, що допомагають робити
неймовірне --- [Emacsrocks](http://emacsrocks.com/){:target="_blank"}.

![Меню менеджера пакетів Emacs](/images/emacs-packages.png)
: Меню менеджера пакетів Emacs.

### 3. Open Source

На відміну від того ж Sublime Text, вам не доведеться платити за Emacs та і вихідний код, <s>в якому
ви все одно ні фіга не зрозумієте</s>, можна правити та брати безпосередню участь в розробці. Та і
віддати $70 [ref] [Sublime Text --- Buy](https://www.sublimetext.com/buy){:rel=noindex}[/ref] за ST
(ми ж всі з вами чесні люди, чи не так?  :)) і користуватись ним як прикладним редактором ІМХО якось
не дуже.

![Emacs vs Vim vs Notepad++](images/emacs-vs-vim-vs-notepad.png)
: Автор коміксу --- Laurent Grégoire


### 4. PROFIT!

Один з прикладів демонстрації можливостей, більше можна переглянути на
сайті [emacsrocks.com](https://emacsrocks.com).

<div class="embed-responsive embed-responsive-16by9">
<iframe class="embed-responsive-item" src="https://www.youtube.com/embed/jNa3axo40qM">
</iframe>
</div> 

## Глобальна проблема --- комбінації клавіш

Кажуть, що в Emacs дуже високий поріг входження, це справді так, проте більшість складнощів
викликані тим, що комбінації клавіш є не звичними та ІМХО катастрофічно незручними. Тому якщо у вас
немає педалей до комп’ютера або щупалець як у восьминога користуватись цим редактором те ще
задоволення.

Річ в тому, що в 1976 році
[ref][Emacs --- Вікіпедія.](https://uk.wikipedia.org/wiki/Emacs){:rel=nofollow}[/ref] коли був
написаний Emacs клавіатура виглядала зовсім по іншому:

![Клавіатура Space-cadet](/images/emacs-keyboard.jpg)
: Клавіатура Space-cadet, одна з перших клавіатур для
[Lisp машин](https://wikipedia.org/){:rel=nofollow}.

## Як не зламати пальці?

На щастя, для вирішення цієї проблеми вже давним-давно був написаний додаток
--- [ergoemacs-mode](https://ergoemacs.github.io/){rel=nofollow target=_blank}, який пропонує
розкладку для звичайних людей (з двома руками і десятьма пальцями). Також він "узвичайнює" багато
операцій, які в Emacs, зважаючи на його цікаву історію, сильно відрізняються від того з чим ми
звикли працювати.

Для користувачів Vim також
наявний [evil-mode](https://bitbucket.org/lyro/evil/wiki/Home){rel=nofollow target=_blank} ---
емулятор vim, але це тема окремого посту.


![Ergoemacs layout](images/ergoemacs-layout-us.png)
: Ергономічні комбінації клавіш від erogemacs-mode

## Конфігурація для початку

За замовчуванням головний файл конфігурації знаходиться за адресою `~/.emacs`, але буде набагато
зручніше перенести його за адресою `~/.emacs.d/init.el`, оскільки всі інші файли (кеш, завантажені
додатки, тощо) зберігаються саме тут.

### Пакети

Так само, як і більшість Linux-дистрибутивів Emacs має власну систему репозиторіїв.

```
:::lisp
;; Підключаємо модуль керування пакетами
(require 'package)

;; Формуємо список джерел звідки будемо тягнути пакети
(setq package-archives '(("gnu" . "https://elpa.gnu.org/packages/")
                         ("marmalade" . "https://marmalade-repo.org/packages/")
                         ("melpa" . "https://melpa.org/packages/")
						 ("org" . "http://orgmode.org/elpa/")))
;; Завантажуємо і ініціалізуємо пакети
(package-initialize)
```

### Use-package --- грамотне керування пакетами


```
:::lisp
(unless (package-installed-p 'use-package)
  (package-install 'use-package))
  
(setq use-package-verbose t)
(require 'use-package)
```

### Ergoemacs --- збереже Ваші пальці

```
:::lisp
(use-package ergoemacs
  :pin gnu
  :init (ergoemacs-mode 1)
  :config (progn 
	    (setq ergoemacs-theme nil)
	    (setq ergoemacs-keyboard-layout "us")
	    (setq ergoemacs-message-level nil) ;; Disabling all debug messages.
	    (ergoemacs-mode 1)))
```

Що ми отримали в результаті:

1. Додали репозиторії, тепер ви можете встановити пакети на ваш смак натиснувши `Alt+A
   package-list-packages`(Alt+X з налаштуваннями за замовчуванням).
2. Встановили use-package, для грамотного керування пакетами (про те як це робити я розповім у 2-ій
   частині).
3. Встановили Ergoemacs --- режим який позбавить вас необхідності користуватись педальками.

Складно і не зрозуміло? Насправді ні! В наступних публікаціях, я покроково розпишу, що і до чого.

## Використані матеріали
2. [Why Emacs's Keyboard Shortcuts are Painful](https://goo.gl/LDjHrl){:rel=nofollow}
3. [Почему Emacs?](http://goo.gl/c3NYy8){:rel=nofollow}

## Посилання