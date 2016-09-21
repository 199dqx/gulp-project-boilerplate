# gulp-project-boilerplate

> gulp 项目的构建模板，gulp 常用插件的配置合集，适合日常小型多页面项目的开发，功能上近似腾讯的 [tmt-workflow](https://github.com/weixin/tmt-workflow)，但更简单并便于修改。


## 功能特征

 - 监听文件变动，自动刷新浏览器 (LiveReload)
 - 合成 CSS Sprite 雪碧图，并输出响应式 css （size 使用 rem，position 使用百分比）
 - 识别合并依赖文件，输出去缓存文件 Reversion (MD5)，自动插入 HTML
 - artTemplate 模板，并使用 TmodJS 将模板预编译
 - Less -> CSS
 - CSS Autoprefixer 前缀自动补全
 - CSS 压缩 cssnano
 - JS 合并压缩
 - HTML 压缩
 - imagemin 图片压缩
 - 一键打包


## 快速使用

### 安装
首先确保已安装 [Node.js](https://nodejs.org/)，以及 [Gulp](https://github.com/gulpjs/gulp/tree/4.0)。

下载或克隆本项目，进入根目录执行： `npm install`


### 执行任务

#### 1.开发任务 `gulp watch`

执行 `gulp watch` 后会发生以下过程：

 - 编译合并部分文件：
 	- `artTemplate -> template.js` 
 	- `合并libs -> lib.js` 
 	- `sprite 图合成 -> sprite.less` 
 	- `less -> css` 
 - 自动监听文件改动，触发浏览器刷新


#### 2.生产任务 `gulp build`

开发完成后，执行 `gulp build` 生成最终文件到 /dist 目录，包含以下过程：

 - LESS/artTemplate 编译
 - CSS/JS/IMG/HTML  压缩合并
 - 文件添加 MD5 版本号 


### 文件结构

```bash

├── gulpfile.js 					// gulp 任务配置文件
│ 								
├── less.sprite.template.mustache 	// gulp.spritesmith 的模板文件
│
└──project 						// 项目文件夹
	├── src 						// 开发目录，`gulp watch` 阶段会监听此目录下的部分文件变动
	│	├── css 					// 存放 Less 文件的目录，只有 main.less 会被编译
	│	│	├── modules 			// less 模块文件夹，包含 reset.less 、 variable.less  等 
	│	│	├── main.less 			// CSS 编译出口文件
	│	│	└── sprite.less 		// 雪碧图合并输出的 less 文件，将被 main.less 引用
	│	│
	│	├── fonts   
	│	├── images
	│	├── js
	│	│	├── lib 				// js 类库文件夹，会合并输出 lib.js
	│	│	├── tplbuild 			//  网页 template 文件合并预编译后的输出文件夹
	│	│	├── base.js 
	│	│	└── a.js, b.js, c.js
	│	│	
	│	├── media
	│	├── slice 					// 切片图片素材，将会进行雪碧图合并
	│	├── sprite 					// 雪碧图图合并后的输出文件夹
	│	├── tpl 					// 网页 template 模板文件夹
	│	│	├── tpl1.html 						
	│	│	└── tpl2.html
	│	│
	│	├── a.html
	│	├── b.html
	│	└── c.html
	│
	└── dist						// 生产目录，由 `gulp build` 任务生成

```





 
