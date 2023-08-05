[![Build status](https://ci.appveyor.com/api/projects/status/xa3bigoee59f33tf?svg=true)](https://ci.appveyor.com/project/malushkru0878/carddelivery-q87i0)

# Домашнее задание к занятию «2.2. Selenide»

## Настройка CI

Настройка CI осуществляется аналогично предыдущему заданию (за исключением того, что файл целевого сервиса теперь называется `app-card-delivery.jar`).

## Задача №1 - Заказ доставки карты

Вам необходимо автоматизировать тестирование формы заказа доставки карты:

![](pic/order.png)

Требования к содержимому полей:
1. Город - [один из административных центров субъектов РФ](https://ru.wikipedia.org/wiki/%D0%90%D0%B4%D0%BC%D0%B8%D0%BD%D0%B8%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%B8%D0%B2%D0%BD%D1%8B%D0%B5_%D1%86%D0%B5%D0%BD%D1%82%D1%80%D1%8B_%D1%81%D1%83%D0%B1%D1%8A%D0%B5%D0%BA%D1%82%D0%BE%D0%B2_%D0%A0%D0%BE%D1%81%D1%81%D0%B8%D0%B9%D1%81%D0%BA%D0%BE%D0%B9_%D0%A4%D0%B5%D0%B4%D0%B5%D1%80%D0%B0%D1%86%D0%B8%D0%B8)
1. Дата - не ранее трёх дней с текущей даты
1. Поле Фамилия и имя - разрешены только русские буквы, дефисы и пробелы
1. Поле телефон - только цифры (11 цифр), символ + (на первом месте)
1. Флажок согласия должен быть выставлен

Тестируемая функциональность: отправка формы.

Поля Город и Дата заполняются через прямой ввод значений (без использования выбора из выпадающего списка и всплывающего календаря).

Условия: если все поля заполнены корректно, то форма переходит в состояние "Загрузки":

![](pic/loading.png)

Важно: состояние загрузки не должно длиться более 15 секунд.

После успешной отправки формы (завершения бронирования) появится всплывающее окно об успешном завершении бронирования:

![](pic/popup.png)

Вам необходимо самостоятельно изучить элементы на странице, чтобы подобрать правильные селекторы. Обратите внимание, что элементы могут быть как скрыты, так и динамически добавляться/удаляться из DOM.

<details>
    <summary>Подсказка</summary>

    Смотрите на `data-test-id`, но помните, что он может быть не у всех элементов.
</details>

<details>
    <summary>Ловушка 😈</summary>

    Дата и время - всегда будут уязвимым местом ваших тестов. Ключевое - если вы их захардкодите, то тест, который работал сегодня, уже может не работать завтра (через неделю, месяц), потому что дата может перейти в разряд условного "прошлого" для приложения и стать невалидной.

    Кроме того, дата и время - это одно из немногих мест в тестах, где вам **иногда** придётся писать логику.
</details>

## Задача №2 - Взаимодействие с комплексными элементами (необязательная)

Большинство систем старается помогать пользователям ускорить выполнение операций: для этого предоставляются формы с автодополнением и элементы вроде календарей.

Проверьте отправку формы используя следующие условия:
1. Ввод 2 букв в поле город, после чего выбор нужного города из выпадающего списка:

![](pic/dropdown.png)

2. Выбор даты на неделю вперёд (начиная от текущей даты) через инструмент календаря:

![](pic/calendar.png)

**Важно: предлагаемая вам задача действительно сложная и потребует от вас достаточно много усилий для решения. Именно поэтому задача перенесена в разряд необязательных.**

P.S. Стоит отметить, что перед автоматизацией вы должны попробовать оценить стоимость автоматизации (в неё же входит и сложность). Но оценивать вы не научитесь, не попробовав автоматизировать.

