# Hooks

## Установка

В простой установке git-hooks нам поможет [husky](https://github.com/typicode/husky), по ссылке есть более подробное описание, как можно использовать.
> npm install husky --save-dev

## Примеры использования

1. Для примера, добавляем в хуки проверку линтеров на commit - [eslint](/files/.eslintrc) и [stylelint](/files/stylelintrc) (это базовые линтеры, которые подходят для большинства проектов, дополнительно можно подключать и другие, [tslint](https://palantir.github.io/tslint/usage/configuration/) например). А также запуск ваших unit-test-ов на push

```json
{
  ...
  "scripts": {
    ...
    "eslint": "./node_modules/.bin/eslint ./path/to/scripts/*.js",
    "stylelint": "stylelint ./path/to/styles/*.scss --syntax scss",
    "lint": "npm run eslint && npm run stylelint",
    "test" "jest"
  },
  "husky":{
    "hooks": {
      "pre-commit": "npm run lint",
      "pre-push": "npm run lint && npm run test"
    }
  } 
  ...
}
```
2. Если вы хотите, что бы перед коммитом ваш код не только проверялся, но и  не забывал форматироваться по заранее заданным правилам - это не сложно реализовать, как пример [.prettier](https://prettier.io/). Предварительно устанавливаем

> npm install --save-dev prettier lint-staged

После этого необходимо добавить нужные поля в наш package.json

```json
{
...
  "scripts": {
    ...
    "stylelint": "stylelint ./path/to/styles/*.scss --syntax scss",
    "test" "jest"
  },
  "lint-staged": {
    "*.{js,json,md}": ["prettier --write", "git add"]
  },
  "husky":{
    "hooks": {
      "pre-commit": "lint-staged && npm run stylelint",
      "pre-push": "npm run test"
    }
  } 
  ...
}
```
