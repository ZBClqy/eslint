# eslint 基本配置

## root

root:true

//默认我们的eslint会向上父文件查找eslintrc文件执行其配置对代码进行检查，但是如果父级上真的有而且和我们项目的冲突会造成不必要的麻烦，所有我们设置root:true告诉我们的eslint默认只在当前文件夹中寻找不会向父级文件夹上寻找

## env

env：{

​	browser:true, 浏览器

​	commonjs:true, 

​	node:true, nodejs

​	es6:true	

}

我们在可能在代码中会使用各种各样版本的js而这些版本的运行环境是不一样的有的是浏览器有的是node所以我们需要向上面一样将想要适配的环境开启，以防eslint检测该环境没有其变量属性。

## extends

extends:["plugin:vue/base","eslint:recommended"]

我们在eslint是可以去继承规则引用包的，里面内置了许多配置好的规则，比如我们的eslint:recommended里面内置了七十条左右的常用规则，我们默认将其继承引用而且它是内置的无需下载，像我们的plugin:vue/base其实是引用了eslint-plugin-vue包，在vue项目中我们需要引入这个包，因为我们的eslint默认是只会对js文件和规则进行处理而不会对我们的vue文件和规则进行处理。

## plugins

plugins:["vue"]

我们在plugins内显示的说明了我们都继承了那些包，比如上面我们继承了eslint-plugin-vue包我们就在plugins中写入数组vue这里可以省略前面的eslint-plugin

## parser

parser:"vue-eslint-parser"

我们前面在extends就说到eslint无法解析除了js外的格式文件，前面我们继承了plugin-eslint-vue来规范我们的vue但是没有解析器,这里我们就需要使用我们的vue-eslint-parser第三方包解析器来解析我们vue让其可以让eslint读取并检查规范。

## parserOptions

parserOptions:{

​	sourceType:"module",

​	ecmaVersion:10,

​	parser:"babel-eslint"

}

我们前面使用了vue-eslint-parser解析器，我们可以在其parserOptions进行更细致的配置，我们用sourceType配置我们js来源默认是script但是我们在vue项目中都是使用的模块化所以我们使用module，然后ecmaVersion来设置我们的js语法的版本，最后前面我们将其解析器设置成vue-eslint-parser但是不是所有的文件都是vue还是会有我们的js而且js文件而且js最新的语法可能eslint不兼容，这时候就要在我们的parserOptions里面在配置一个parser用于解析我们的js和其高级的语法。

## globals

globals：{

​	document:true,

​	navigator:true,

​	window:true

}

我们的eslint有点死板的会去查看使用的变量是否定义如果未定义就报错，包括我们内置的全局变量属性也不放过。所以我们就要使用globals去声明我们要使用的内置全局变量属性表示我们要使用不进行检测。

## rules

我们可以在里面配置我们的检测规则