# Ionic Storage
A simple key-value Storage module for Ionic apps based on LocalForage, with out-of-the-box support for SQLite. This utility makes it easy to use the best storage engine available without having to interact with it directly. Currently the ordering is SQLite, IndexedDB, WebSQL, and LocalStorage.

If you want to perform arbitrary SQL queries and have one of the best storage options around, we recommend using the [Ionic Native SQLite plugin](http://ionicframework.com/docs/v2/native/sqlite/) directly. This engine no longer supports the `query` feature underneath as it was not portable and only worked for SQLite anyways.

### Usage

To use this in your Ionic 2/Angular 2 apps, either start a fresh Ionic project which has it installed by default, or run:

```bash
npm install @ionic/storage
```

Then edit your NgModule declaration in `src/app/app.module.ts`) to add `Storage` as a provider:

```typescript
import { Storage } from '@ionic/storage';

@NgModule({
  declarations: [
    ...
  ],
  imports: [
    IonicModule.forRoot(MyApp)
  ],
  bootstrap: [IonicApp],
  entryComponents: [
    ...
  ],
  providers: [ Storage ] // Add Storage as a provider
})
export class AppModule {}
```

Now, you can easily inject `Storage` into a component:

```typescript
import { Component } from '@angular/core';

import { NavController } from 'ionic-angular';

import { Storage } from '@ionic/storage';

@Component({
  selector: 'page-home',
  templateUrl: 'home.html'
})
export class HomePage {

  constructor(public navCtrl: NavController, public storage: Storage) {

  }

}
```

To set an item, use `Storage.set(key, value)`:

```javascript
this.storage.set('name', 'Mr. Ionitron');
```

To get the item back, use `Storage.get(name).then((value) => {})` since `get()` returns a Promise:

```javascript
this.storage.get('name').then((name) => {
  console.log('Me: Hey, ' + name + '! You have a very nice name.');
  console.log('You: Thanks! I got it for my birthday.');
});
```

