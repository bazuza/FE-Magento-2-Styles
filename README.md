## Compile LESS with Grunt

### Installing and configuring Grunt
1. Install [node.js](https://nodejs.org/en/) to any location on your machine.
2. Install Grunt CLI tool globally and locally. To do this, run the following command in a command prompt: `npm install -g grunt-cli`, `npm install grunt --save-dev`  
3. Install (or refresh) the `node.js` project dependency, including Grunt, for your Magento instance. To do this, run the following commands in a command prompt:
```
cd <your_Magento_instance_directory>
npm install
npm update
```
4. Add your theme to Grunt configuration. To do this, in the `dev/tools/grunt/configs/themes.js` file, add your theme to module.exports like following:
```
module.exports = {
    ...
    <theme>: {
        area: 'frontend',
        name: '<Vendor>/<theme>',
        locale: '<language>', 
        files: [
            'css/styles-m',
            'css/styles-l'
        ],
        dsl: 'less'
    ...
    },
```
5. (Optional) If you want to use Grunt for "watching" changes automatically, without reloading pages in a browser each time, install the [LiveReload extension](http://livereload.com/extensions/) in your browser.

### Grunt commands:
* `grunt clean:<theme>` Removes the theme related static files in the `pub/static` and `var` directories.
* `grunt exec:<theme>` Republishes symlinks to the source files to the `pub/static/frontend/<Vendor>/<theme>/<locale>` directory.
* `grunt less:<theme>` Compiles `.css` files using the symlinks published in the `pub/static/frontend/<Vendor>/<theme>/<locale>` directory
* `grunt watch` Tracks the changes in the source files, recompiles `.css` files

## Compile LESS with Gulp
<table>
<tr><th></th><th>Gulp</th><th>Grunt</th></tr>
<tr><td>Compilation of all themes (10 files):</td><td>16sec</td><td>33sec</td></tr>
<tr><td>Custom theme compilation (2 files)</td><td>4.5s</td><td>11.2s</td></tr>
</table>

### Installation
1. Download as a zip file or clone [this](https://github.com/subodha/magento-2-gulp).
2. Copy `gulpfile.js` and `package.json` in to the root directory
3. Install gulp globaly and locally using `npm install -g gulp-cli`, `nmp install gulp --save-dev`
4. Install modules: run a command in a root directory of your project `npm install`.
5. Compilation: `gulp less --<theme> --live (with live reload)`
6. Watcher: `gulp watch --<theme> --live (with live reload)`
7. For using [liveReload](http://livereload.com/) install extension for your browser


**Note**

:exclamation: _Don't remove grunt modules (You must use `gunt exec:<theme>` command for republishes symlinks to the source files)_

## Resources:
* [Compile LESS with Grunt](http://devdocs.magento.com/guides/v2.0/frontend-dev-guide/css-topics/css_debug.html)
* [Compile LESS with Gulp](https://github.com/subodha/magento-2-gulp)
