# Front-end development specification

> Feel free to create pull requests to add content. Open issues to discuss ideas, or get clarification.

## Для чего это нужно?

> We should be on the same page

Чтобы front-end отдел превратился во front-endman-а.

### Кто такой front-endman?

Он скрывается во front-end отделе.

Он не совершает ошибок, его код всегда идеален.

Он следует лучшим стандартам и использует лучшие практики.

Он может работает с любыми технологиями.
В то же время он не распыляется благодаря тому, что он состоит из множества частей
и каждая его часть знает свою технологию на столько хорошо, что может написать книгу.

Он [SuperDRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself). Все, что он сделал один раз
в следующий сделает в три раза быстрее.

Он знает все героические [принципы](https://www.artima.com/weblogs/viewpost.jsp?thread=331531).

### Основные принципы

Основные принципы front-endman-а это:

#### Реюзабельность

Разработка ведется с помощью модулей, которые можно скачать из каталога,
если в каталоге еще нет нужного вам модуля, то он разрабатывается с расчетом на
то, чтобы добавить его в каталог для использования в будущем.

#### Автоматизация

> Все, ... автоматизировать, ... автоматизировать.

Тестирование,
развертывание проекта,
[настройка ОС](https://github.com/vlad-yaremenko/dotfiles),
приготовление кофе,
должно быть максимально быстрым и требовать минимальных телодвижений, и временных затрат.

### Front-endman required knowledge

- Intermediate english level
- HTML5, CSS3, JavaScript, SVG
- Responsive Web, SCSS, BEM
- Git & GitLab
- HTTP(S), RESTful APIs, SSH
- NPM, Gulp, Webpack
- ES6, TypeScript
- Basic terminal usage, Personal text editor (WebStorm, Vim, Sublime Text, etc.)
- Testing
- Data structures & Algorithms
- GOF Design patterns, Architectural patterns
- Regular Expressions
- SOLID, YAGNI, KISS etc

Тут [больше](https://codeburst.io/the-2018-web-developer-roadmap-826b1b806e8d)

### Personal qualities

- Концентрация. Он изучает выбранную тему до конца. Он не умеет все и сразу.
- Для фиксации прогресса он пишет статью на изученную тему и делится ей с обществом.
- Он может признать свои проблемы. У него есть список проблем и он стремительно идёт к их устранению.

## Architecture

Создание архитектуры ведётся в [draw.io](https://www.draw.io/)

На планирование архитектуры в обязательном порядке выделяется **от 8-ми часов**.

### Stages

При разработке архитектуры нужно:

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

## README

Все проекты сопровождаются [README.md](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) файлом в котором описаны:

- Название проекта
- Короткое описание
- Homepage
- Ссылку на систему баг трекинга
- Ссылку на репозиторий
- Инструкция по установке зависимостей и настройке окружения
- Команды для:
  - Старта разработки. Запуск watch-еров
  - Сборки
  - Запуска тестов
- Указаны основные технологии
- Указаны поддержка браузеров

## Browsers support

Если заказчик не определил поддержку браузеров, то по умолчанию мы поддерживаем:

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

Для линтинга кода package.json имеет несколько обязательных dev-зависимостей.

#### Project

```json
{
  "name": "project-name",
  "version": "0.0.1",
  "scripts": {
    "start": "Start development process",
    "publish": "Create build for production",
    "test": "Run tests (unit, lint, ...)",
    "stylelint": "stylelint \"**/*.scss\" --syntax scss"
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

Для разметки страницы используется HTML5.

## Styles

Для написания стилей используется [шаблонизатор SCSS](https://sass-lang.com/)

Для поддержания code style подключается [файл](/dotfiles/.stylelintrc) конфигураций [StyleLint](https://stylelint.io/)

Настройки StyleLint формируются из [правил StyleLint](https://stylelint.io/user-guide/rules/)
и дополнительных плагинов:

- [stylelint config standard](https://github.com/stylelint/stylelint-config-standard) - основа для правил StyleLint
- [stylelint-scss](https://github.com/kristerkari/stylelint-scss#list-of-rules)
- [stylelint-no-unsupported-browser-features](https://www.npmjs.com/package/stylelint-no-unsupported-browser-features) - проверяет поддержку браузером написанных правил

Для запуска StyleLint необходимо установить зависимости

```bash
# Install dependencies
npm i -D stylelint stylelint-config-standard stylelint-no-unsupported-browser-features stylelint-scss

# Run linting
stylelint ./path/to/styles/*.scss --syntax scss
```

### Methodologies

При разработке стилей используется [BEM](http://getbem.com/) методология.

## JavaScript

### ES6+

Код должен соответствовать требованием [Airbnb](https://github.com/airbnb/javascript).

В каждый проект, для избежания элементарных ошибок, подключается [конфигурационный](/dotfiles/.eslintrc) файл [ESLint](https://eslint.org/).

## Development process

### Code linting

#### *Lint files list

- [ESLint](/dotfiles/.eslintrc)
- [StyleLint](/dotfiles/.stylelintrc)

Подключенные *Lint файлы будут делать невозможным билд/коммит проекта без соблюдения их правил.

### TODO

Все изменения, которые нужно внести в код или реализовать, должны быть описаны в TODO комментариях, в тех местах, где нужно реализовать функционал или внести изменения.

Это делается для того, чтобы не держать в голове все изменения и дать другим разработчикам понимание того, что нужно изменить или не трогать.

При продакшн сборке все TODO комментарии удаляются.

### Comments

Избегайте бессмысленного комментирования кода, имена переменных и функций должны говорить сами за себя.

Comments – Do not write comments for what you are doing, instead write comments on why you are doing.
Specify about any hacks, workaround and temporary fixes. Additionally, mention pending tasks
in your to-do comments, which can be tracked easily.

При продакшн сборке все комментарии удаляются.

### Branch flow

TODO: Coming soon. Describe branch flow

TODO: Use git hooks for automatization https://developer.ibm.com/node/2017/08/31/use-eslint-project/

### Code review

Первое, что должен проверить ревьювер - работает ли функционал так, как должен.

#### Основные задачи code review

- Распространить знания по команде
- Научиться думать, как остальные члены команды
- Повысить качество и поддерживаемость кода

#### Все, что можно автоматизировать, должно быть автоматизированно

Отлов ошибок нужно предоставить тестам

Следование code style-у должен проверять *lint-ер. Это повысит читаемость кода и упростит его
поддержку.

#### Ревьювер

> Find problems, Not solutions

Важно искать возможные проблемы в решении, а не стараться максимально оптимизировать код (если
это не является целью). Если решение уж очень плохое, сообщить автору об этом, понять как он к этому
пришел и помочь найти другое решение.

Code review - high priority task.

**Максимальное** время на ревью **1 час**. Далее код отправляется на доработку или принимается

Не просматривай более 500 строк кода за раз

Если что-то копируется больше 2-х раз, это может быть копипастом

##### Проверь:

- Работает ли функционал так как описано в требованиях
- Maintainability
  - Читается ли код как проза
  - Нарушения семантики - делает ли класс/метод то что написано в его названии
- Тестируемость
- Логические ошибки
- Архитектурные ошибки
- Возможности для упрощения, использования паттернов.
- Idiomatic - используются ли все возможности языка, фреймворка
- Использование плохих практик
- Team code convention
- No hard coding, use constants/configuration values
- Зависимости между классами/компонентами/модулями. Везде ли они нужны?
- Reliability - отлов исключений
- Security
  - Are all data inputs checked (for the correct type, length, format, and range) and encoded?
  - Where third-party utilities are used, are returning errors being caught?
  - Are output values checked and encoded?
  - Are invalid parameter values handled?
- Performance
- Usability & User experience

#### Author, please

> Don't meke me think

Одна цель - один коммит

Title - коротко описывает функционал.

Description - описывает что было изменённо, на что нужно обратить внимание. Содержит описание таска.

**Не squash коммиты до окончания ревью**

**Делай code review самостоятельно перед коммитом** (просматривай `git diff`)

Постарайтесь ответить на каждый комментарий

Merge request должен содержать не более 400 строк кода

Удаляйте закомментированный код. Его можно легко восстановить с помощью VCS.

#### Feedback mechanism

Используйте комментарии в merge request. По окончанию code review сообщите от этому автору в личном сообщении.

Instead of explaining the entire solution to developers during the code review process, simply
share the links of relevant websites or encourage them to research on the
internet by providing keywords.

---

[Read me](https://medium.com/@palantir/code-review-best-practices-19e02780015f)

### Testing

TODO: Coming soon

Проект должен включать в себя Unit тесты для избежания повторяющихся ошибок и ускорения процесса разработки.

Unit тестами нужно покрывать:
- Основной функционал
- Часто используемые компоненты
- Сервисы с бизнес логикой

TODO: Полное покрытие тестами выполняется для компонентов из каталога

Все тесты запускаются на основе [Karma](https://karma-runner.github.io/2.0/index.html).

Для тестирования используется TODO: Выбрать Mocha/Jasmine

Jest, Enzyme, Google PageSpeed, GT Metrix, SEO Site Checkup, Pingdom Website Speed Test, YSlow, Webpage Test
TDD, E2E testing, Integration testing, Functional testing, UI testing, Acceptance tests, Components tests, Service tests, Visual testing.

#### BrowserStack

Для тестирования кроссбраузерности используется BrowserStack.

Для работы с ним нужно установить [chrome extension](https://chrome.google.com/webstore/detail/browsersync/odccdjehkinjebnjnkpbjeplabccchfe),
прописать в настройках расширения `https://www.browserstack.com/`

![Browsersync options](https://i.imgur.com/RCZzT84.png)

и зайти в общий [BrowserStack](https://www.browserstack.com/).

В случае, если BrowserStack занят, страница будет заблокирована, пока BrowserStack не освободится.

Все пожелания по расширению оставляем [тут](https://github.com/vlad-yaremenko/browsersync-extension/issues)

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

## Issues

Suggestions/improvements [welcome](https://github.com/vlad-yaremenko/front-end-specification/issues)!
