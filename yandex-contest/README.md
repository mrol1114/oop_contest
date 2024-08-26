# Порядок работы над переносом заданий на платформу Яндекс.Контест

## Ознакомьтесь с документацией

Есть видеокурс по работе в системе. Просмотрите уроки, имеющие отношение к созданию задаче и их проверке.

<https://cs.hse.ru/olymp/yacontest>

## Поэкспериментируйте с задачей в песочнице

Вам будет выдан доступ к задаче с названием Sandbox-ВашаФамилия, в которой вы можете проводить эксперименты.

В некоторых задачах требуются иллюстрации. Изучите возможности платформы Яндекс.Контест по вставке изображений.

## Заведите Issue на гитхаб-аккаунте со списком доработок, которые нужно сделать по вашей задаче

Это опциональный пункт, нужен, чтобы вы не забыли, что нужно сделать. Посмотрите примеры уже существующих Issues,
чтобы было понятно, что туда обычно записывают.

## Отредактируйте описание задачи

Некоторые задачи в нынешнем виде получают данные из внешнего файла, а не из stdin,
однако с небольшими доработками можно изменить условие так, чтобы 
программа принимала данные из stdin, а выводила в stdout.

В этом случае нужно отредактировать описание задачи на гитхабе.
В качестве примера рассмотрим [условие задачи FindText](example1.md).
Условие изменено так, чтобы программа могла принимать данные не только из файла, но и из stdin.

Так как программы будут тестироваться автоматически, условие задачи должно быть таким, чтобы студенту понятен формат входных и выходных данных.

Например, если программе подаются на вход целые числа, то нужно указать, каким образом эти числа разделяются (пробелами, табуляциям или же переносами строки).
На C++ при чтении из `std::cin` операцией `>>` пробелы, табуляции и символы переноса строки пропускаются.
На других языках программирования чтение таких данных может оказаться более трудоёмким.
В этом случае можно упростить жизнь студенту, сказав, что числа разделяются одним пробелами.

То же самое касается и выходных данных: лучше тоже уточнить формат выходных данных:

- как должны разделяться выводимые данные?
- с какой точностью должны выводиться числа с плавающей запятой.
- какой текст должен выводиться в случае ошибки (или ошибок)

В подавляющем большинстве заданий следует использовать английский язык, чтобы студенту не пришлось решать проблемы с юникодом.

Для редактирования markdown-файлов рекомендую использовать Visual Studio Code. Установите расширения:

- Markdown All in One
- markdownlint
- Code Spell Checker
- Russian - Code Spell Checker.

В некоторых задачах может потребоваться внести дополнительные ограничения на работу программы, чтобы ее проще было протестировать.
Например, в лабиринте может быть несколько (или даже очень много) кратчайших путей между двумя точками.
Чтобы не писать кастомный матчер, можно потребовать, чтобы при наличии нескольких вариантов сделать шаг вдоль кратчайшего маршрута, они выбирались в следующем порядке: вверх, вниз, влево, вправо.

## Отправьте Pull Request (PR) (на мерж в ветку master-new)

Свои изменения вносите в отдельную ветку, ответвлённую от master-new.

Оформите запрос на слияние ваших изменений c описанием задачи в ветку master-new.

- Один PR должен включать изменения по одной задаче.
- Если вы внесли изменения в несколько задач, оформите два разных PR (каждый в отдельной ветке), каждый из которых содержит изменения только по одной задаче.
  Так вы получите меньше изменений и ваши правки будут приняты быстрее.

Пока ваш PR проверяется, приступайте к следующему шагу - редактированию задачи в Яндекс.Contest

## Отредактируйте задачу на платформе Яндекс.Contest

Перенесите текст условия задачи на платформу (лучше всего в формате markdown). Составьте для задачи набор тестовых файлов, позволяющих качественно проверить работу программы.

Обязательно должны быть тестовые файлы, проверяющие работу программы на данных, указанных в условии задачи (в Яндекс.Контест можно часть тестов сделать открытыми).

Тестовые данных должны проверять работу программы на разных классах эквивалентности, на граничных данных. Тесты должны пропускать правильно написанную программу, а написанную с ошибками — отлавливать.

В некоторых программах (например, Car и TV) лучше больше небольших пар input-output, чем один или 2 больших файла.

При переносе условия задачи обратите внимание на форматирование. Возможно, его потребуется подправить. Например, изменить уровень вложенности заголовков (в github-репозитории они, скорее всего глубже, чем на Yandex.Contest).

## Проверьте работу эталонной программы

Напишите свою (или возьмите у одногруппников, решивших задачу) программу и проверьте, пройдёт ли она все проверки.

Внесите в программу изменения, заведомо делающие её некорректной или частично реализованной, и убедитесь, что тесты отлавливают эти ошибки. 
Например, в программе TV можно закомментировать или сделать неверной проверку граничных условий и убедиться, что тесты обнаруживают этот недостаток.