# Правила оформления кода на Java

## Файлы, пакеты

* Имена классов должны быть существительными, первые буквы всех слов — заглавные.
* Имена папок, файлов и пакетов состоят только из строчных букв. Слова в многословных названиях разделяются подчеркиванием
* Используйте UTF-8,  как кодировку для Ваших исходных файлов
* Описание файла должно быть в самом начале. Далее идут объявления операторов package и import, причем каждый блок разделяется пустой строкой.

## Отступы, длина строки, переносы строк

* Отступы должны составлять строго 4 пробельных символа (ASCII, 0x20)
* Символы табуляции не используются для отступов 
* Длина строки не должна превышать 100 символов.
* При превышении длины строки, выражение разбивается согласно следующим правилам:
     1. перенос после запятой;
     2. перенос перед оператором;
     3. используйте отступ в 8 пробелов для обозначения второй строки разделенного выражения. 
     4. Последующие строки выравниваются по второй строке либо добавляются новые 8 пробелов для обозначения вложенности.

Пример:

int result = someLongExpression(this, expression, on, first, line)     
        + someLongExpression(this, expression, on, seccond, line) 

## Расположение блоков, операторов, пробелы, скобки

* Определение переменных нужно располагать в начале блока, а не «ждать» первого использования переменной. Инициализация должна производиться, по возможности, сразу.

void myMethod() {
    int count = 0; // beginning of method block
    if (condition) {
        int int2; // beginning of "if" block
        ...
    }
}

* Между именем метода и скобками для списка параметров нет пробела.

getStaffList(String name)

* Параметры разделяются пробелом.

getStaffList(String name, int count)

* Пробелы окружают любой оператор.

res = getCount();
(a > 10) ? b : c;

* Ключевое слово и следующая за ним скобка ( должны разделяться пробелом.

while (b < 100) {
    …
}

* Открывающаяся скобка { располагается на той же строке, что и сигнатура метода/заголовок if, while-блока и т.п.

* Закрывающаяся скобка } выровнена по строке начала данного блока.

public Collection getStaffList(String name) {
    Collection contacts = Contact.getList(name, RoleHelper.ROLE_AGENT, null,
    AccessLevel.getStaffDiaryEditLevel(), 0, MAX_NUMBER);
    return ListHelper.getLabelValueList(contacts);
}

* Методы разделяются пустой строкой, объявления свойств класса располагаются по одному на строку.

* На строке располагается только один оператор.

if (b) {
    return result;
}

## Имена методов, переменных

* Названия методов должны быть глаголами, первая буква должна быть строчной, первые буквы внутренних слов — заглавные.
* Имена переменных должны начинаться со строчной буквы, внутренние слова — с заглавной.
* Придерживайтесь следующих названий полей:
     * Не static и не public имена начинаются c «m».
     * static поля начинаются с «s».
     * Другие поля начинаются с буквы нижнего регистра.
     * Поля public static final (константы) пишутся полностью в верхнем регистре, с использованием подчеркивания (ALL_CAPS_WITH_UNDERSCORES)


## Структурирование кода

* Методы должны быть короткими, и выполнять только одну задачу (к примеру, почти любой цикл уже достоин того, чтобы вынести его в особый метод).
* Имена методов должны быть самодокументированными.
* Шаблоны ООП должны применяться для структурирования и облегчения восприятия.


## Комментарии/Javadoc

* Описание файла в самом начале. - комментарий.
* Для описания классов  используется Javadoc, лучше начинать фразу с описательного глагола 3-го лица. 
* Не нужно описывать Javadoc для тривиальных get и set методов
* Если метод делает что-то более сложное (например, соблюдение неких ограничений, или если его действия имеют важный эффект вне его самого), тогда его стоит задокументировать. Вообще, любой метод, полезно описывать в Javadoc, неважно public он или нет. Public методы являются частью API, и поэтому необходимы описания в Javadoc
* Стиль TODO. Используйте комментарии TODO для кода, который является временным, краткосрочным, или хорошим, но не идеальным. Комментарий должен включать в себя «TODO:», например:

// TODO: Remove this code after the UrlTable2 has been checked in.

// TODO: Change this to use a flag instead of a constant.

Если ваш комментарий имеет вид «В будущем сделать что-то», то убедитесь, что он включает в себя конкретную дату (1 января 2011 года), или конкретное событие «Удалить после выхода версии 2.1».


## Импорты

Порядок операторов импорта следующий:
     1. Android импорты.
     2. Сторонние импорты (com, junit, net, org).
     3. java и javax.

Для полного соответствия настройкам IDE, импорты должны иметь следующий вид:
* Отсортированы по алфавиту внутри каждой группы.
* Заглавные буквы должны быть впереди букв нижнего регистра (например, Z перед a).
* Главные группы должны разделяться пустой строкой.


## Локальные переменные 

* Область видимости локальных переменных должна сводиться к минимуму. Делая это, вы улучшаете читаемость и поддерживаемость кода, а также уменьшаете вероятность ошибок.
* Каждая переменная должна объявляться в самом глубоком блоке, который окружает все возможные места использования переменной.

* Локальные переменные должны объявляться в том месте, где впервые необходимо её использовать. 
* Почти каждая локальная переменная нуждается в инициализаторе. 
* Отложите объявление локальной переменной, пока вы не узнаете, как ее инициализировать.

! Исключение:

Это исключение касается блока `try-catch`. Если переменная инициализируется при помощи оператора return метода, который выбрасывает проверяемое исключение, то она должна инициализироваться в блоке try. Если же переменная должна использоваться вне блока try, тогда она объявляется перед ним, неважно, знаете ли вы, как её нужно инициализировать, или нет:

// Instantiate class cl, which represents some sort of Set 
Set s = null;
try {
    s = (Set) cl.newInstance();
} catch(IllegalAccessException e) {
    throw new IllegalArgumentException(cl + " not accessible");
} catch(InstantiationException e) {
    throw new IllegalArgumentException(cl + " not instantiable");
}

// Exercise the set 
s.addAll(Arrays.asList(args));



Однако этот случай можно обойти при помощи инкапсуляции блока try-catch в методе.

Set createSet(Class cl) {
    // Instantiate class cl, which represents some sort of Set 
    try {
        return (Set) cl.newInstance();
    } catch(IllegalAccessException e) {
        throw new IllegalArgumentException(cl + " not accessible");
    } catch(InstantiationException e) {
        throw new IllegalArgumentException(cl + " not instantiable");
    }
}

...

// Exercise the set 
Set s = createSet(cl);
s.addAll(Arrays.asList(args));



* Переменные в циклах должны объявляться внутри самого оператора, если только нет непреодолимой причины этого не делать.
< for (int i = 0; i <= n; i++) {
    doSomething(i);
}

for (Iterator i = c.iterator(); i.hasNext(); ) {
    doSomethingElse(i.next());
} >