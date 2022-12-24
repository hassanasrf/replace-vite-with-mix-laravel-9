# Replace Vite with Mix in Laravel 9.2

If you are starting a Laravel 9.2 project and don’t want to use Vite you can easily remove it and revert back to Laravel Mix.

Start by adding the following to your project root directory webpack.mix.js

```php
const mix = require('laravel-mix');

/*
 |--------------------------------------------------------------------------
 | Mix Asset Management
 |--------------------------------------------------------------------------
 |
 | Mix provides a clean, fluent API for defining some Webpack build steps
 | for your Laravel application. By default, we are compiling the Sass
 | file for the application as well as bundling up all the JS files.
 |
 */

mix.js('resources/js/app.js', 'public/js')
    .sass('resources/sass/app.scss', 'public/css')
    .sourceMaps();
```

Then modify your package.json file:

```Original```
```php
"scripts": {
    "dev": "vite",
    "build": "vite build"
},
```

```Modified```
```php
"scripts": {
    "dev": "npm run development",
    "development": "mix",
    "watch": "mix watch",
    "watch-poll": "mix watch -- --watch-options-poll=1000",
    "hot": "mix watch --hot",
    "prod": "npm run production",
    "production": "mix --production"
},
"devDependencies": {
    "@popperjs/core": "^2.10.2",
    "axios": "^0.25",
    "bootstrap": "^5.1.3",
    "laravel-mix": "^6.0.6",
    "lodash": "^4.17.19",
    "postcss": "^8.1.14",
    "resolve-url-loader": "^5.0.0",
    "sass": "^1.32.11",
    "sass-loader": "^11.0.1"
}
```

That should be it. Now you can run npm run dev or npm run development etc. to use Laravel Mix.
