# Front-end Boilerplate

A boilerplate for building web projects with [Gulp](https://gulpjs.com/), [Babel](https://babeljs.io/), SASS, jQuery and Owl-carousel(edit and remove if Owl-carousel is not needed).
The Boilerplate makes it easy to turn features on and off, so you can reuse it for all of your projects without having to delete or modify tasks.

## Features

### Gulp

- Concatenate, minify, and lint JavaScript.
- Next generation JavaScript compiling and concatenating to ES5 or any required version with Babel.
- Compile, minify, autoprefix, and lint Sass.
- Automatically add headers and project details to JS and CSS files.
- Optimize SVGs.
- Create polyfilled and non-polyfilled versions of JS files.
- Copy static files and folders into your dist directory.
- Watch for file changes, and automatically recompile build and reload webpages.

### SASS

- **Basic structure**: Folder structure and partials.
- **Autoprefix:** Adding vendor prefixes for you.
- **Vendors**: Bootstrap and Owl-carousel sass files included.

### JS

- **Basic structure**: Folder structure and partials.
- **Vendors**: Bootstrap and Owl-carousel sass files included.
- **Babel**: Compiling and concatenating to one ES5 file for better page load speed and cross-browser support.

## Getting Started

### Dependencies

Note: if you've previously installed Gulp globally, run `npm rm --global gulp` to remove it.

Make sure these are installed first.

- [Node.js](http://nodejs.org/)
- [Gulp Command Line Utility](http://gulpjs.com/) `npm install --global gulp-cli`

### Quick Start

1. In bash/terminal/command line, `cd` into your project directory.
2. Run `npm install` to install required files and dependencies.
3. When it's done installing, run one of the task runners to get going:
   - `gulp` manually compiles files.
   - `gulp watch` automatically compiles files and applies changes using BrowserSync when you make changes to your source files.

**Try it out**. After installing, run gulp to compile some test files into the dist directory. Or, run gulp watch and make some changes to see them recompile automatically.

## Documentation

Add your source files to the appropriate **src** subdirectories. Gulp will process and compile them into **dist**.

- JavaScript files in the src/js directory will be compiled to dist/js. Files in subdirectories under the js folder will be concatenated and convert into ES5. For example, files in js/main will compile into main.js.
- Files in the **src/sass** directory will be compiled to **dist/css**.
- SVG files placed in the **src/svg** directory will be optimized with SVGO and compiled into **dist/svg**.
- Files and folders placed in the **copy** directory will be copied as-is into the **dist** directory.

## Options and Settings

Gulp Boilerplate makes it easy to customize for projects without having to delete or modify tasks.

Options and settings are located at the top of the **gulpfile.js**.

### Settings

Set features under the settings variable to true to turn them on (default), and false to turn them off.

    /**
    * Settings
    * Turn on/off build features
    * eachJS : for rendering each files of js folder
    */

    var settings = {
    	clean: true,
    	scripts: true,
    	polyfills: true,
    	styles: true,
    	svgs: true,
    	copy: true,
    	reload: true,
    	eachJS: false
    };

## Folder structure

Adjust the `src_path` and `dist_path` paths for all of the Gulp tasks under the paths variable. Paths are relative to the root project folder.

var src_path = 'src/';  
var dist_path = 'dist/';

    .
    ├─ src
    |   ├── svg
    |   ├── copy
    |   ├── js
    |   |      main                             # Taget folder of js files for compiling JS.
    |   |       ├──contact
    |   |       |   ├── index.js
    |   |       ├──map
    |   |       |   ├── index.js
    |   |       ├──slider
    |   |       |   ├── index.js
    |   |       ...
    |   ├── sass
    |   |       styles.scss                     # Taget file for compiling SASS.
    |   |       ├──base
    |   |       |   ├── __base-master.scss
    |   |       |   ├── _reboot.scss
    |   |       |   ...
    |   |       ├──components
    |   |       |   ├── __components-master.scss
    |   |       |   ├── _button.scss
    |   |       |   ...
    |   |       ...
    ├─ dist
    |   ├── svg                                 # Automated compressed svg folder.
    |   ├── js
    |   |   ├── main.js                         # Automated build single js file from src/main folder.
    |   ├── css
    |   |   ├── styles.css                      # Automated build single css file from src/scss/styles.scss file.
    ├─ gulpfile.js
    ├─ package.json
    ├─ .babelrc                                 # Babel settings file.
    ...
    Note: Need to create image task with svg

## Naming convention ([BEM](https://en.bem.info/methodology/))

### Block

- Blocks are logically and functionally independent page components.
- Blocks can be nested inside any other blocks.
- Blocks can be moved around on a page, moved between pages or projects.
- Blocks can be reused.

Eg: `menu`

### Element

- Elements are a constituent part of a block that can't be used outside of it.
- Elements can be nested inside each other
- An element is always part of a block, not another element.
- An element is an optional block component.
- The element name describe it's purpose.

Eg: `menu__item`

### Modifier

- A modifier is an entity that defines the appearance, state, or behavior of a block or element.
- A modifier is always part of a block or element.
- A modifier should change the appearance, behavior, or state of the entity, not replace it.
- The use of modifiers is optional.
- Modifiers are similar in essence to HTML attributes. The same block looks different due to the use of a modifier.
- Modifiers can be changed in runtime (for example, as a reaction to a DOM event of the block), or via other blocks.

**Types of Modifiers**

_Boolean_

> Used when only the presence or absence of the modifier is important, and its value is irrelevant.
> If a Boolean modifier is present, its value is assumed to be true.
Eg: `menu_hidden`, `menu__item_visible`

_Key-Value_

> Used when the modifier value is important.
Eg: `menu_theme_islands`, `menu_item_type_radio`

### Class nomenclature

- Names are written in lowercase latin letters.
- Words are separated by a hyphen (-).
- The block name describe it's purpose
- The block name defines the namespace for its elements and modifiers.
- The element name is separated from the block name by a double underscore (\_\_).
- The modifier name is separated from the block or element name by a single underscore (\_).
- The modifier value is separated from the modifier name by a single underscore (\_).
- For boolean modifiers, the value is not included in the name.

### File nomenclature

- Each block corresponds to a single directory.
- The code of modifiers and elements is stored in separate files.
- The files of modifiers and elements are stored in separate directories.
- The block directory is the root directory for the subdirectories of its elements and modifiers.
- Names of element directories begin with a double underscore (\_\_).
- Names of modifier directories begin with a single underscore (\_).
