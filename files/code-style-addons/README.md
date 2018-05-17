# Additional code style conventions

Можно ипользовать также дополнительные соглашения по стилю кода, принятые в JS-сообществе, но не отраженные в официальных style guide вроде [Air BnB](https://github.com/airbnb/javascript), или [Angular](https://angular.io/guide/styleguide).

## Naming

### Async entities naming
Переменные, константы, поля классов, указывающие на асинхронные сущности, именуются с суффиксом $, как это принято в Angular community. Это могут быть Promise, Observable, EventEmitter, Subject и т.п.
```html
<!-- inside an html template -->
<div *ngFor="let item of items$ | async">{{item.title}}</div>
```

```typescript
// inside some class
packages$: Observable<NpmPackageInfo[]>;
private searchText$ = new Subject<string>();
```
