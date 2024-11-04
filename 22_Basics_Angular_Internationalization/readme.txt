// Let's see what is Internationalization


What is Internationalization?
    -> Internationalization (i18n) in Angular refers to the process of designing your application so that it can be easily adapted to various languages and regions without requiring engineering changes. This includes translating text, formatting dates, numbers, and currencies according to local conventions.


Using JSON data for internationalization allows you to store translations in a structured way, making it easier to manage and update.

Steps to Implement i18n with JSON Data in Angular

1. Create JSON Translation Files: You can create separate JSON files for each language. For example, you might have en.json for English and fr.json for French.

en.json:
{
  "HELLO": "Hello",
  "WELCOME": "Welcome to our application!",
  "GOODBYE": "Goodbye"
}

fr.json:
{
  "HELLO": "Bonjour",
  "WELCOME": "Bienvenue dans notre application !",
  "GOODBYE": "Au revoir"
}

2. Install Required Package: You'll need the @angular/common package, which usually comes with Angular. If you want to use a library for managing translations, consider using ngx-translate.

npm install @ngx-translate/core @ngx-translate/http-loader

3. Set Up Translation Module: In your Angular module, set up the translation loader.

import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { HttpClientModule } from '@angular/common/http';
import { TranslateModule, TranslateLoader } from '@ngx-translate/core';
import { TranslateHttpLoader } from '@ngx-translate/http-loader';
import { AppComponent } from './app.component';

export function HttpLoaderFactory(http: HttpClient) {
  return new TranslateHttpLoader(http);
}

@NgModule({
  declarations: [AppComponent],
  imports: [
    BrowserModule,
    HttpClientModule,
    TranslateModule.forRoot({
      loader: {
        provide: TranslateLoader,
        useFactory: HttpLoaderFactory,
        deps: [HttpClient]
      }
    })
  ],
  bootstrap: [AppComponent]
})
export class AppModule {}

4. Use the Translate Service in a Component: In your component, you can use the TranslateService to set the default language and get translations.

import { Component } from '@angular/core';
import { TranslateService } from '@ngx-translate/core';

@Component({
  selector: 'app-root',
  template: `
    <h1>{{ 'HELLO' | translate }}</h1>
    <p>{{ 'WELCOME' | translate }}</p>
    <button (click)="switchLang('en')">English</button>
    <button (click)="switchLang('fr')">Français</button>
  `
})
export class AppComponent {
  constructor(private translate: TranslateService) {
    this.translate.setDefaultLang('en');
    this.translate.use('en'); // set the default language to English
  }

  switchLang(lang: string) {
    this.translate.use(lang);
  }
}


Explanation of the Code

1. Translation Files: The JSON files contain key-value pairs where keys represent the text identifiers and values represent the translated text.

2. Translation Module Setup: The TranslateModule is set up in the AppModule with an HTTP loader to fetch the JSON translation files.

3. Translate Service: In the AppComponent, the TranslateService is used to set the default language and change languages based on user input (via buttons). The translate pipe is used in the template to display the translated text.

4. Language Switching: When a user clicks a button, the switchLang method is called to change the language. The displayed text updates automatically.


Summary

Internationalization (i18n): Allows your application to support multiple languages and regional settings.
JSON Translation Files: Store translations in structured JSON files, making it easy to manage.
ngx-translate: A popular library for handling translations in Angular apps.
Using i18n with JSON data helps create a more user-friendly application for diverse audiences!