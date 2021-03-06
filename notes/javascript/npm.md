[node.js](node.md)

## NPM - Node Package Manager
<a href="https://www.npmjs.com/">
  <img src="https://raw.githubusercontent.com/gmetais/YellowLabTools/master/doc/img/npm-logo.png" width="300">
</a>

**[D3.js](d3.md)** | **[Express.js](express.md)** | **[ghost](ghost.md)** | **[Knex](knex.md)** | **[React.js](react/index.md)** | **[three.js](threejs.md)**

Uses 'package.json' to record dependencies, & install them after downloading a project.

### Commands
- `npm i moduleName`: Installs module(s)
- `npm i moduleName --save`: Installs module(s) & save in package.json
- `npm i moduleName -D` or `npm i moduleName --save-dev`: Installs module(s) & saves in package.json in 'devDependencies'
- `npm -g ls` or `npm list -g`: Prints list of all globally installed modules
- `npm list -g | grep express`: List global modules, pipe to grep & search for moduleName (express)
- `npm -g ls --depth=0`
- `npm uninstall moduleName --save`: Uninstalls module & deletes reference in package.json



### Ramda
- A js library for functional programming
- automatically curries

### List
- express-session (session storage)
- express-generator
- body-parser
- cookie-parser
- dotenv
- hbsfy
- browserify
- simpleget
- superagent
- xhr
- bluebird (promises?)
- promise
- jade, handlebars, hyper-script
- inu
- bcrypt-node, bcrypt
- lodash, Ramda, underscore
- cylon
- body-parser
- moment
- passport
- jQuery
- pg
- sqlite3
- keypress
- cylon-ble
- babel, babelify, babel-preset-es2015, babel-preset-react
- budo
- gh-pages
- react, react-dom
- uglifyify
- node-emoji
- yandex-translate-api
- is-url
- unirest
- smokestack


**devDependencies** (see also [testing](../testing.md))
- watchify
- cheerio
- forever
- nightwatch
- supertest
- tape, tap-closer
- tap-spec
- nodemon

See also [building / bundling](../building.md)
