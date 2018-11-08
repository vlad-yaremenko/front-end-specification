# Hooks

## Дополнительные примеры использования

Если вы еще больше хотите автоматизировать свой проект, то для вас есть еще пару интересных примеров использования:

1. Если вы хотите, что бы перед коммитом ваш код не только проверялся, но и не забывал форматироваться по заранее заданным правилам - это не сложно реализовать, как пример [.prettier](https://prettier.io/). Предварительно устанавливаем

> npm install --save-dev prettier lint-staged

После этого необходимо добавить нужные поля в наш package.json

```json
{
  "name": "project-name",
  "version": "0.0.1",
  "scripts": {
    "start": "Start development process",
    "publish": "Create build for production",
    "test": "jest"
  },
  "lint-staged": {
    "*.js": ["./node_modules/.bin/eslint --fix", "prettier --write", "git add"],
    "*.scss": ["stylelint --fix", "prettier --write", "git add"],
    "*.{json,md}": ["prettier --write", "git add"]
  },
  "husky":{
    "hooks": {
      "pre-commit": "lint-staged",
      "pre-push": "npm test"
    }
  }
}
```
2. Если по какой-то причине вам необходимо проигнорировать  механизм хуков, вы можете добавить флаг no-verify перед своим коммитом:

> git commit -m "bypass git hooks" --no-verify

3. Так же, если ваш проект основан на определенном фреймворки, настроить хуки не составит труда. Для примера, расмотрим проект основанный на Angular CLI:

```json
{
  "name": "project-name",
  "version": "0.0.1",
  "scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "test": "ng test",
    "lint": "ng lint && npm run lint:styles",
    "lint:styles": "stylelint .src/app/*/**/*.scss -- syntax scss && stylelint ./src/styles.scss --syntax scss",
    "e2e": "ng e2e"
  },
  "lint-staged": {
    "*.scss": [
      "stylelint ./src/app/*/**/*.scss --fix && ./src/styles.scss --fix",
      "git add"
    ],
    "src/**/*.ts": ["tslint --fix", "git add"]
  },
  "husky":{
    "hooks": {
      "pre-commit": "lint-staged && ng lint",
      "pre-push": "ng test && ng e2e"
    }
  }
}
```

