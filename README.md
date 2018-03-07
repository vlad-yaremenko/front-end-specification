# Frone-end development specification

> Feel free to create pull requests to add content. Open issues to discuss ideas, or get clarification.

## Для чего это нужно?

> We should be on the same page

Чтобы front-end отдел превратился во front-endman - а.

### Кто такой front-endman?

Он скрывается во front-end отделе.

Он не совершает ошибок, его код всегда идеален.

Он следует лучшим стандартам и использует лучшие практики.

Он может работает с любыми технологиями.
В то же время он не распыляется благодаря тому, что он состоит из множества частей
и каждая его часть знает свою технологию на столько хорошо, что может написать книгу.

Он [SuperDRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself). Все, что он сделал один раз в седующий он сделает в три раза быстрее.

Он знает все героические [принципы](https://www.artima.com/weblogs/viewpost.jsp?thread=331531).

### Front-endman required knowledge

- HTML/CSS/JavaScript
- Responsive Web
- SCSS
- BEM
- SVG
- Git - Version control
- HTTP(S)
- RESTful APIs
- SSH
- Basic terminal usage
- Personal text editor
- Testing
- Data structures & Algorithms
- GOF Design patterns
- Architectural patterns
- SOLID, YAGNI, KISS etc
- Regular Expressions
- ES6
- TypeScript
- NPM
- Gulp
- Webpack

Тут [больше](https://codeburst.io/the-2018-web-developer-roadmap-826b1b806e8://codeburst.io/the-2018-web-developer-roadmap-826b1b806e8d)

### Personal qualities

- Концентрация. Он изучает выбранную тему до конца. Он не умеет все и сразу.
- Для фиксации прогресса он пишет статью на изученную тему и делится ей с обществом.
- Он может признать свои проблемы. У него есть список проблем и он стремительно идёт к их устранению.

## Architecture

Создание архитектуры ведётся в [draw.io](https://www.draw.io/)

На планирование архитектуры в обязательном порядке выделяется **от 8 - ми часов**.

### Stages

При разработки архитектуры нужно:

- [Выбрать методологию разработки](#software-development-methodologies)
- Выбрать стек технологий
- Разбить проект на отдельные модули
- Описать работу сервисов
- Продумать взаимодействие между сервисами и модулями

### Rules

При написании модуля избегать **сильной привязки к окружению**.

**Работу с сервисами выносить в корневые модули страниц**. Исключать вызовы сервисов в компонентах (input, select, dropdown).

Все строковые значения (url, идентификаторы) **выносить в constants**.

Любые функции общего назначения (форматирование даты, подготовка данных) **выноситься в helper**.

**Get** методы и функции должны **возвращать значение**.

## Software development methodologies

- [ATDD](https://en.wikipedia.org/wiki/Acceptance_test%E2%80%93driven_development "Acceptance test–driven development")
- [BDD](https://en.wikipedia.org/wiki/Behavior-driven_development "Behavior-driven development")
- [CCO](https://en.wikipedia.org/wiki/Extreme_programming_practices#Collective_code_ownership "Extreme programming practices")
- [CI](https://en.wikipedia.org/wiki/Continuous_Integration "Continuous Integration")
- [CD](https://en.wikipedia.org/wiki/Continuous_Delivery "Continuous Delivery")
- [DDD](https://en.wikipedia.org/wiki/Domain-driven_design "Domain-driven design")
- [PP](https://en.wikipedia.org/wiki/Pair_Programming "Pair Programming")
- [Stand-up](https://en.wikipedia.org/wiki/Stand-up_meeting "Stand-up meeting")
- [TDD](https://en.wikipedia.org/wiki/Test-driven_development "Test-driven development")

## README

Все проекты сопровождаются [README.md](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) файлом в котором описаны:

- Название проекта
- Короткое описание
- Homepage
- Ссылку на систему баг трекинга
- Сыылку на репозиторий
- Инструкция по установке зависимостей и настройке окружения
- Команды для:
  - Старта разработки. Запуск watch - еров
  - Сборки
  - Запуска тестов
- Указаны основные технологии
- Указаны поддержка браузеров

## Browsers support

Если заказчик не определил браузерную поддержку, то по умолчанию мы поддерживаем:

![Chrome](https://raw.githubusercontent.com/alrra/browser-logos/master/src/chrome/chrome\_48x48.png) | ![Firefox](https://raw.githubusercontent.com/alrra/browser-logos/master/src/firefox/firefox\_48x48.png) | ![IE](https://raw.githubusercontent.com/alrra/browser-logos/master/src/edge/edge\_48x48.png) |![Edge](https://raw.githubusercontent.com/alrra/browser-logos/master/src/edge/edge\_48x48.png) | ![Opera](https://raw.githubusercontent.com/alrra/browser-logos/master/src/opera/opera\_48x48.png) | ![Safari](https://raw.githubusercontent.com/alrra/browser-logos/master/src/safari/safari_48x48.png)
---      | ---      | ---   | ---      | ---      | ---      |
Latest ✔ | Latest ✔ | 10+ ✔ | Latest ✔ | Latest ✔ | Latest ✔ |

## Base setup

### .files

- [.gitignore](dotfiles/.gitignore)
- [.*lint](#code-linting)
- .env - Описывает переменные окружения для node.js проектов
- .babelrc
- [.editorconfig](dotfiles/.editorconfig) - Синхронизирует настройки редакторов. Hужно установить [плагин](http://editorconfig.org/#download) для своего редактора, если его нет.

### Package.json

package.json находится в корневой директории и является стартовой точкой проекта.

#### Project

```json
{
  "name": "project-name",
  "version": "0.0.1",
  "scripts": {
    "start": "Start development process",
    "publish": "Create build for production",
    "test": "Run tests (unit, lint, ...)"
  },
  "dependencies": {
    "name": "version"
  },
  "devDependencies": {
    "name": "version"
  }
}
```

Тут больше [package.json](https://docs.npmjs.com/files/package.json)

## Markup

Для разметки страницы ислользуется HTML5.

## Styles

Для написания стилей используется [шаблонизатор SCSS](https://sass-lang.com/)

В проект с использованием SCSS подключается [файл](/dotfiles/.stylelintrc) конфигараций [StyleLint](https://stylelint.io/)

### Methodologies

При разработке стилей используется [BEM](http://getbem.com/) методология.

## JavaScript

### ES6+

Код должен соответствовать требованием [Airbnb](https://github.com/airbnb/javascript).

В каждый проект, для избежания елементарных ошибок, подключается [конфигурационный](/dotfiles/.eslintrc) файл [ESLint](https://eslint.org/).

## Development process

### Code linting

#### *Lint files list

- [ESLint](/dotfiles/.eslintrc)
- [StyleLint](/dotfiles/.stylelintrc)

Подключенные *Lint файлы будут делать невозможным билд/коммит проекта без соблюдения их правил.

### TODO

Все изменения, которые нужно внести в код или реализовать, должны быть описаны в TODO коментариях, в тех местах, где нужно реализовать функционал или внести изменения.

Это делается для того, чтобы не держать в голове все изменения и дать другим разработчикам понимание того, что нужно изменить или не трогать.

При продакшн сборке все TODO коментарии удаляются.

### Comments

Избегайте бессмысленного коментирования кода, имена переменных и функций должны говорить сами за себя.

При продакшн сборке все коментарии удаляются.

### Branch flow

TODO: Coming soon. Describe branch flow

TODO: Use git hooks for automatization https://developer.ibm.com/node/2017/08/31/use-eslint-project/

### Code review

TODO: Coming soon. Describe code review process

### Testing

TODO: Coming soon

Проект должен включать в себя Unit тесты для избежание повторяющихся ошибок и ускорения процесса разработки.

Unit тестами нужно покрывать:
- Основной функционал
- Часто используемые компоненты
- Сервисы с бизнес логикой

TODO: Полное покрытие тестами выполняется для компонентов из каталога

Все тесты запускаются на основе [Karma](https://karma-runner.github.io/2.0/index.html).

Для тестирования извользуется TODO: Выбрать Mocha/Jasmine

Jest, Enzyme, Google PageSpeed, GT Metrix, SEO Site Checkup, Pingdom Website Speed Test, YSlow, Webpage Test
TDD, E2E testing, Integration testing, Functional testing, UI testing, Acceptance tests, Components tests, Service tests, Visual testing.

#### BrowserStack

Для тестирования кроссбраузерности используется BrowserStack.

Для работы с ним нужно установить [chrome extension](https://chrome.google.com/webstore/detail/browserstack-automatizati/lnbbklihpjghcboodnmcehadmhhphdea) и зайти в общий [BrowserStack](https://www.browserstack.com/).

В случае, если BrowserStack занят другим разработчиком или тестировщиком, страница будет заблокирована, пока BrowserStack не освободится.

### Good breeding

При разработке UI делается акцент на качество UX.
Вот некоторые примеры хорошего UX:

- Закрывать попапы по нажатию esc
- Возможность ходить по всем элементам управления с помощью tab
- Возможность управления стрелочками в селекте
- Реакция на focus
- Активная ссылка не должна нажиматься дважды
- Вывод сообщений об ошибке

У нас [тут больше](http://bfy.tw/Gt9G)

## Continius integration

TODO: Coming soon codecov, travis, jenkins, circle.

## Post-deployment maintenance

TODO: Coming soon

## TODO

- Опмсать использование модулей
- TypeScript
- Project generator
- Branch flow strategy
- UML
- Continius integration
- Post-deployment maintenance
- Browsers support
- Code review
- Provide сode examples for architecture
- Описать принципы составления архитектуры проекта
- Describe development practices
- Describe package.json settings for npm modules
- Autoprefixer settings
- Describe required devDependencies
- Добавить пример README.md файла
- Describe HTML
- Describe BEM
- Describe SCSS

## Author

| [![twitter/_VladYaremenko](https://pbs.twimg.com/profile_images/675676400527933440/1S0w_hoY_200x200.jpg)](https://twitter.com/_VladYaremenko "Follow @_VladYaremenko on Twitter") |
|---|
| Vlad Yaremenko <vladyaremenko95.vy@gmail.com> |

## Issues

Suggestions/improvements [welcome](https://github.com/vlad-yaremenko/front-end-specification/issues)!
