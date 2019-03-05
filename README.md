# sails-generate-scaffold

**Note:** This module requires Sails **v0.10.0-rc8** or higher.

A `scaffold` generator for use with the Sails command-line interface.  A `scaffold` generates a rudimentary model, CRUD controller actions (e.g. index, new, create, edit, update, and destroy), and corresponding views of a Sails project.   The `scaffold` generator will also create a policy that enables flash messages for errors on the new and edit views. 

### To install:

```sh
$ npm install sails-generate-scaffold
```

Next open up the `.sailsrc` file located in the root of your sails project.  Add the `scaffold` by typing:

```javacript
{
  "generators": {
    "modules": {
    	"scaffold": "sails-generate-scaffold"
    }
  }
}
```

### To create a scaffold

##### On the command line

```sh
$ sails generate scaffold <a name for your scaffold> <optional: attributename:attributetype> <optional: --force>
```

Example:

```sh
$ sails generate scaffold user name:string age:integer email:email
```

The first argument will be the `model` and `controller` name.  You can add any number of model attributes and types. Finally, you can overwrite an existing scaffold by using the `--force` parameter.

### To config Routes

add a link to each Model into `view/pages/scaffold.js`

Example :
```html
 <a href="/User" class="btn btn-lg btn-success spar-list">User</a>
```
Add the following routes to `config/routes.js`
```js
'/scaffold'                    : { view: 'pages/scaffold' },
```
and for each models :
```js
'GET /[ModelName]'             : '[ModelName]Controller.index',
'GET /[ModelName]/new'         : '[ModelName]Controller.new',
'POST /[ModelName]/create'     : '[ModelName]Controller.create',
'POST /[ModelName]/update'     : '[ModelName]Controller.update',
'POST /[ModelName]/destroy'    : '[ModelName]Controller.destroy',
'GET /[ModelName]/show/:id'    : '[ModelName]Controller.show',
'GET /[ModelName]/edit/:id'    : '[ModelName]Controller.edit',
```
replace `[ModelName]` by the model name used when you created the scaffold ( ex: `User` ) 

### More Resources

- [Stackoverflow](http://stackoverflow.com/questions/tagged/sails.js)
- [#sailsjs on Freenode](http://webchat.freenode.net/) (IRC channel)
- [Twitter](https://twitter.com/sailsjs)
- [Professional/enterprise](https://github.com/balderdashy/sails-docs/blob/master/FAQ.md#are-there-professional-support-options)
- [Tutorials](https://github.com/balderdashy/sails-docs/blob/master/FAQ.md#where-do-i-get-help)
- <a href="http://sailsjs.org" target="_blank" title="Node.js framework for building realtime APIs.">SailsJs.org</a>


### License

**[MIT](./LICENSE)**
&copy; 2014 [irlnathan](http://github.com/irlnathan) & contributors

As for [Sails](http://sailsjs.org)?  It's free and open-source under the [MIT License](http://sails.mit-license.org/).

![image_squidhome@2x.png](http://i.imgur.com/RIvu9.png)
