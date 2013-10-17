#JSDoc 3
-------
##简介
JSDoc3是生成JavaScript的API文档的工具.利用Mozilla Rhino(java)引擎,从JavaScript代码的注释中提取API情报,生成HTML文档.注释以/\*\*开头，以\*/结束.关键字以@开头.  
***Mozilla Rhino:****https://developer.mozilla.org/ja/docs/Rhino_Overview*

##安装
**因为Mozilla Rhino是Java写的,所以事先得安装Java环境.**
#######1.下载和安装
npm install git://github.com/jsdoc3/jsdoc.git
#######2.执行
JSDoc的根目录下执行     **jsdoc \*.js**
   
	./jsdoc --help
	OPTIONS:
	-t, --template <value>		The name of the template to use. Default: the "default" template
	-c, --configure <value>		The path to the configuration file. Default: jsdoc __dirname + /conf.json
	-e, --encoding <value>		Assume this encoding when reading all source files. Default: utf8
	-T, --test		Run all tests and quit.
	-d, --destination <value>		The path to the output folder. Use "console" to dump data to the console. Default: ./out/
	-p, --private		Display symbols marked with the @private tag. Default: false
	-r, --recurse		Recurse into subdirectories when scanning for source code files.
	-l, --lenient		Continue to generate output if a doclet is incomplete or contains errors. Default: false
	-h, --help		Print this message and quit.
	-X, --explain		Dump all found doclet internals to console and quit.
	-q, --query <value>		A query string to parse and store in env.opts.query. Example: foo=bar&baz=true
	-u, --tutorials <value>		Directory in which JSDoc should search for tutorials.
	-v, --version		Display the version number and quit.
	--verbose		Display verbose output for tests
	--match <value>		Only run tests containing <value>
	--nocolor		Do not use color in console output from tests

##JSDoc语法
###Namepaths in JSDoc 3
在使用JsDoc之前，首先要了解一个概念就是namepath。本质上讲，namepath是JSDoc注释里明确变量的实例成员，静态成员或者内部成员的机制。
###Tutorials机制

###追加Readme文件
jsdoc C:\path\to\my\JS\project\sourceFiles C:\path\to\my\JS\project\README.md

###配置

	// You must remove the comments before adding these options to your .json file
	{
    "tags": {
        "allowUnknownTags": true
    },
    "source": {
        "include": [],
        "exclude": [],
        "includePattern": ".+\\.js(doc)?$",
        "excludePattern": "(^|\\/|\\\\)_"
    },
    "plugins": [],
    "templates": {
        "cleverLinks": false,
        "monospaceLinks": false
    },
    "opts": {
        "template": "default",            // same as -t default
        "encoding": "utf8",               // same as -e utf8
        "destination": "./out/",          // same as -d ./out/
        "recurse": true,                  // same as -r
        "tutorials": "path/to/tutorials", // same as -u path/to/tutorials, default "" (no tutorials)
        "query": "value",                 // same as -q value, default "" (no query)
        "private": true,                  // same as -p
        "lenient": true,                  // same as -l
        // these can also be included, though you probably wouldn't bother
        // putting these in conf.json rather than the command line as they cause
        // JSDoc not to produce documentation. 
        "version": true,                  // same as --version or -v
        "explain": true,                  // same as -X
        "test": true,                     // same as -T
        "help": true,                     // same as --help or -h
        "verbose": true,                  // same as --verbose, only relevant to tests.
        "match": "value",                 // same as --match value, only relevant to tests.
        "nocolor": true                   // same as --nocolor, only relevant to tests
    }
	}
###CommonJS Modules

###Tag
	Inline tags
	All about inline tags {@link ...}, {@linkplain ...}, {@linkcode ...}, {@tutorial ...}.
	@abstract
	This member must be implemented (or overridden) by the inheritor.
	@access
	Specify the access level of this member - private, public, or protected.
	@alias
	Treat a member as if it had a different name.
	@augments
	This object adds onto a parent object.
	@author
	Identify the author of an item.
	@borrows
	This object uses something from another object.
	@callback
	Document a callback function.
	@classdesc
	Use the following text to describe the entire class.
	@constant
	Document an object as a constant.
	@constructor
	This function is intended to be called with the "new" keyword.
	@constructs
	This function member will be the constructor for the previous class.
	@copyright
	Document some copyright information.
	@default
	Document the default value.
	@deprecated
	Document that this is no longer the preferred way.
	@desc
	Describe a symbol.
	@enum
	Document a collection of related properties.
	@event
	Document an event.
	@example
	Provide an example of how to use a documented item.
	@exports
	Identify the member that is exported by a JavaScript module.
	@external
	Document an external class/namespace/module.
	@file
	Describe a file.
	@fires
	Describe the events this method may fire.
	@global
	Document a global object.
	@ignore
	[todo] Remove this from the final output.
	@inner
	Document an inner object.
	@instance
	Document an instance member.
	@kind
	What kind of symbol is this?
	@lends
	Document properties on an object literal as if they belonged to a symbol with a given name.
	@license
	[todo] Document the software license that applies to this code.
	@link
	Inline tag - create a link.
	@member
	Document a member.
	@memberof
	This symbol belongs to a parent symbol.
	@method
	Describe a method or function.
	@mixes
	This object mixes in all the members from another object.
	@mixin
	Document a mixin object.
	@module
	Document a JavaScript module.
	@name
	Document the name of an object.
	@namespace
	Document a namespace object.
	@param
	Document the parameter to a function.
	@private
	This symbol is meant to be private.
	@property
	Document a property of an object.
	@protected
	This member is meant to be protected.
	@public
	This symbol is meant to be public.
	@readonly
	This symbol is meant to be read-only.
	@requires
	This file requires a JavaScript module.
	@returns
	Document the return value of a function.
	@see
	Refer to some other documentation for more information.
	@since
	When was this feature added?
	@static
	Document a static member.
	@summary
	A shorter version of the full description.
	@this
	What does the 'this' keyword refer to here?
	@throws
	Describe what errors could be thrown.
	@todo
	Document tasks to be completed.
	@tutorial
	Insert a link to an included tutorial file.
	@type
	Document the type of an object.
	@typedef
	Document a custom type.
	@variation
	Distinguish different objects with the same name.
	@version
	Documents the version number of an item.

##例子
#####jsdoc book.js
	book.js
	/**
	 * Represents a book.
	 * @constructor
	 */
	function Book(title, author) {
	}
	/**
	 * Represents a book.
	 * @constructor
	 * @param {string} title - The title of the book.
	 * @param {string} author - The author of the book.
	 */
	function Book(title, author) {
	}

##JSDoc结构和原理