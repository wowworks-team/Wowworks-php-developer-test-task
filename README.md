# Тестовое задание на вакансию php разработчика в компанию wowworks
						
Необходимо сделать конвертер PDF в HTML слайдер. Основной алгоритм заключается в следующем:
						
1. Открываем страницу, которая содержит форму для загрузки PDF.
2. Выбираем PDF файл, нажимаем кнопку «Конвертировать».
3. Появляется «полоса загрузки», которая в процентах показывает процесс конвертации. (реализация этого пункта необязательна, но будет плюсом).
4. После того как процесс завершен, открывается новая страница на которой отображается HTML слайдер. В качестве слайдов используются изображения страниц PDF файла.
5. Также на странице слайдера есть кнопка «Скачать», при нажатии на которую скачивается zip архив, содержащий:						
  * index.html, который содержит слайдер.
  * папку images, в которой хранятся изображения, конвертированные из PDF
  * папку assets, в которой хранятся необходимые ресурсы, например JS- библиотека слайдера.
6. После генерации архива оставлять ссылку для просмотра слайдера и повторного скачивания архива, доступную в течение 30 минут после генерации.
7. Так же необходимо реализовать REST API метод для получения списка ссылок изображений конкретного слайдера (по его id) для генерации кастомных слайдеров на сторонних сайтах (json).

### Требования / Ограничения	

##### PDF				
* Ориентация – портретная;
* Количество страниц – не больше 20;
* Размер файла – не более 50 Мб.
						
##### Технологии				
* PHP, HTML, JS;
* Возможно использование готовых классов и библиотек;
* Framework – предпочтительно Yii2 или без framework’ов; 
* Возможно использование exec();
* Можно использовать composer;
* Должны быть unit тесты;
* В проекте должны быть тесты, которые проверяют REST API (behat или codeception);
* Проект должен проходить проверку https://github.com/squizlabs/PHP_CodeSniffer со стилем PSR2;
* Проект должен проходить проверку https://github.com/phpstan/phpstan;
* По REST API должна быть документация в формате https://swagger.io/;
* Комментарии в коде – приветствуются.
						
##### Результат				
* Ссылка на код на Github / BitBucket;
* Как плюс, ссылка на работающий пример.

## Критерии приемки

По каждому критерию можно получить только фиксированный балл, внутри одного критерия баллы не суммируются.

### C1. Deploy

| Описание  | Балл |
| --------- | ----:|
| нету никаких инструкций | 0 |
| есть README.md | 0.5 |
| использован vagrant | 0.75 |
| использован docker | 1 |
| есть docker-compose.yml | 1.5 |

### C2. Сodestyle

| Описание  | Балл |
| --------- | ----:|
| нету | -1 |
| соблюден какой-либо codestyle | 0.5 |
| PSR2 | 1 |
| phpcs --standard=PSR2 не выдает ошибок | 1.75 |
| корректно настроен phpcs.xml.dist | 2 |

### C3. Phpstan

| Описание  | Балл |
| --------- | ----:|
| не исправлены ошибки phpstan level=0 | 0 |
| исправлены ошибки phpstan level=0 | 1 |
| настроен phpstan.neon. `vendor/bin/phpstan analyse -l 0 -c phpstan.neon <directories>` не показывает ошибок, где `<directories>` - папки с бизнес логикой, исправлять ошибки в `vendor`, либо в системных файлах фреймфорка не надо | 1.5 |

### C4. Composer

| Описание  | Балл |
| --------- | ----:|
| в проекте нету composer.json | 0 |
| в проекте есть composer.json, но некоторые библиотеки подключены не через него | 0.5 |
| все сторонние библиотеки подключены через composer.json | 1 |

### C5. REST API

| Описание  | Балл |
| --------- | ----:|
| отсутствует | -0.5 |
| присутствует, есть замечания | 0.5 |
| присутствует, нету замечаний | 1 |

### C6. Swagger documentation

| Описание  | Балл |
| --------- | ----:|
| отсутствует | 0 |
| присутствует, есть замечания | 0.5 |
| присутствует, нету замечаний | 1 |

### C7. MVC pattern

| Описание  | Балл |
| --------- | ----:|
| отсутствует | -0.5 |
| присутствует, есть замечания | 0.5 |
| присутствует, нету замечаний | 1 |


### C8. DRY principle

| Описание  | Балл |
| --------- | ----:|
| нарушен | -0.5 |
| есть замечания | 0.5 |
| нету замечаний | 1 |

[опционально] При желании можно прогнать проект через phpcpd (https://github.com/sebastianbergmann/phpcpd).

### C9. SOLID principle

| Описание  | Балл |
| --------- | ----:|
| нарушен | 0 |
| есть замечания | 0.5 |
| нету замечаний | 1 |

### C10. Global variable

| Описание  | Балл |
| --------- | ----:|
| используются global переменные в явном виде | -1 |
| есть неявное использование  | 0 |
| никак не используются | 1 |

### C11. Неоправданный static

| Описание  | Балл |
| --------- | ----:|
| есть замечания | 0 |
| нету замечений | 2 |

Способ проверки: написать чистый unit тест на класс/метод/функцию, внутри которой будет использоваться static метод/свойство.

### C12. Magic const
[Wikipedia: Магическое число (программирование)](https://ru.wikipedia.org/wiki/%D0%9C%D0%B0%D0%B3%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B5_%D1%87%D0%B8%D1%81%D0%BB%D0%BE_(%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5)#%D0%9F%D0%BB%D0%BE%D1%85%D0%B0%D1%8F_%D0%BF%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D0%BA%D0%B0_%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F)

| Описание  | Балл |
| --------- | ----:|
| есть замечания | -1 |
| нету замечений | 1 |

### C13. Бизнес-логика в классах ActiveRecord

| Описание  | Балл |
| --------- | ----:|
| бизнес логика написана в классе ActiveRecord | 0 |
| бизнес логика вынесена из классов ActiveRecord | 2 |

### C14. Толстый контроллер

| Описание  | Балл |
| --------- | ----:|
| толстый контроллер | 0 |
| тонкий контроллер | 2 |

### C15. Dependency Injection

| Описание  | Балл |
| --------- | ----:|
| отсутствует | 0 |
| присутствует, есть замечания | 2 |
| присутствует, нету замечаний | 4 |

### C16. Acceptance tests

| Описание  | Балл |
| --------- | ----:|
| отсутствуют | 0 |
| присутствуют | 1 |
| есть на все endpoints | 2 |
| 100% code coverage (`vendor/bin/codecept run --coverage --coverage-xml --coverage-html`) | 2 |

### C17. Unit tests

| Описание  | Балл |
| --------- | ----:|
| отсутствуют | -0.5 |
| написаны на codeception unit | 1 |
| написаны на phpunit, есть phpunit.xml.dist | 1.5 |
| использован Mockery | 2 |
| тесты на самом деле unit, codecoverage > 50% | 3 |

## Список литературы
* https://docs.docker.com/get-started/
* https://docs.docker.com/compose/
* https://www.php-fig.org/psr/
* https://github.com/squizlabs/PHP_CodeSniffer/wiki
* https://github.com/phpstan/phpstan
* https://getcomposer.org/doc/00-intro.md
* https://swagger.io/docs/
* https://codeception.com/quickstart
* https://github.com/sebastianbergmann/phpcpd
* https://phpunit.de/documentation.html
* https://github.com/mockery/mockery
* https://refactoring.guru/ru
* Стив Макконнелл. Совершенный код.
* https://ru.wikipedia.org/wiki/Design_Patterns
* http://wiki.c2.com/?GlobalVariablesAreBad
