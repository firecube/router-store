<a name="1.1.0"></a>
# [1.1.0](https://github.com/ngrx/router-store/compare/v1.0.0...v1.1.0) (2016-08-30)


### Bug Fixes

* **actions:** Added show action to export ([#10](https://github.com/ngrx/router-store/issues/10)) ([5a1ed83](https://github.com/ngrx/router-store/commit/5a1ed83))


### Features

* **actions:** Added handling of an array for router actions ([#12](https://github.com/ngrx/router-store/issues/12)) ([3b4b827](https://github.com/ngrx/router-store/commit/3b4b827))



<a name="1.0.0"></a>
# [1.0.0](https://github.com/ngrx/router-store/compare/v0.0.1...v1.0.0) (2016-08-27)


### Features

* **router-store:** Provide bindings to connect [@angular](https://github.com/angular)/router ([2af0ed4](https://github.com/ngrx/router-store/commit/2af0ed4)), closes [#3](https://github.com/ngrx/router-store/issues/3)


### BREAKING CHANGES

* router-store: Router API has changed internally

BEFORE:

Use the `routerReducer` when providing `Store`:
  ```ts
  import { provideStore } from '@ngrx/store';
  import { routerReducer } from '@ngrx/router-store';
  
  
  export const storeProvider = provideStore({
    // Your reducers go here,
    router: routerReducer
  });
  ```

Install the bindings providers after you setup the router providers:
  ```ts
  import { connectRouterToStore } from '@ngrx/router-store';
  
  bootstrap(App, [
    storeProvider,
    provideRouter(routes),
    connectRouterToStore()
  ]);
  ```

AFTER:

Use the `routerReducer` when providing the `StoreModule.provideStore` and add the `RouterStoreModule.connectRouter()` to the `@NgModule.imports`:

  ```ts
  import { StoreModule } from '@ngrx/store';
  import { routerReducer, RouterStoreModule } from '@ngrx/router-store';

  @NgModule({
    imports: [
      BrowserModule,
      StoreModule.provideStore({ router: routerReducer }),
      RouterStoreModule.connectRouter()
    ],
    bootstrap: [ AppComponent ]
  })
  export class AppModule {
  }
  ```

BEFORE:

```ts
import {routerActions} from '@ngrx/store';

store.dispatch(routerActions.go('/path', 'query=string'));
store.dispatch(routerActions.replace('/path', 'query=string'));
store.dispatch(routerActions.search('query=string'));
```

AFTER:

```ts
import {routerActions} from '@ngrx/store';

store.dispatch(routerActions.go('/path', { query: 'string' ));
store.dispatch(routerActions.replace('/path', { query: 'string' ));
store.dispatch(routerActions.search({ query: 'string' ));
```



<a name="0.0.1"></a>
## 0.0.1 (2016-05-13)



