<!-- 

$theme: gaia
template: gaia

-->

Angular2基础
===
---
介绍
===
Angular2是对Angular 1.X的一次重写。
主要在性能，组件化上有了实质性的提升。

即承继了Angular 1的优势，有弥补了Angular 2的劣势。

功能更加的丰富，工具链更加的成熟

采用了新的开发语言TypeScript

---
安装
===
Angular 有方便的命令行工具叫 `Angular CLI`。

安装方式：

```
npm install -g @angular/cli
```

这个时候你将获得一个叫`ng`的命令。

你可以使用`ng`命令实现很多angular的操作。

---
ng 命令行
===
执行ng命令，会出来很多选项。

&gt; ng

```
ng build <options...>
  Builds your app and places it into the output path (dist/ by default).
  aliases: b
  --target (String) (Default: development) Defines the build target.
    aliases: -t <value>, -dev (--target=development), -prod (--target=production), --target <value>
  --environment (String) Defines the build environment.
```

里有很多内容

---
创建项目
===

```
ng new my-app
```
执行tree命令查看目录：

```
eric@eric-ThinkPad-X220:~/ng/my-app$ tree
.
├── e2e
├── karma.conf.js
├── package.json
├── protractor.conf.js
├── README.md
├── src
├── tsconfig.json
└── tslint.json
```
---

运行项目
===

```
cd my-app
ng serve --open
```
<p style="text-align:center"><img src="./images/angular2/running.png"/>
</p>

---
修改代码
===
在`./src/app/app.component.ts`文件里

```
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'app';
}

```

---
将 app修改成 "my app":

<p style="text-align:center"><img src="./images/angular2/app2.png"/>
</p>

---
在`src/app/app.component.css`文件里添加
```
h1 {
  color: #369;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 250%;
}
```
---

我们得到: 

<p style="text-align:center"><img src="./images/angular2/css.png"/>
</p>

---
项目说明-根目录
===

e2e: 测试目录
src: 项目源代码目录
karma.conf.js: 单元测试配置文件
package.json: 项目配置文件
protractor.confjs: E2E测试配置文件
README.md: 项目自说明文件
tsonfig.json: TypeScript配置文件
tslint.json: TypeScript语法检验规则

---
项目说明-src目录
===
```
src/
├── app                 ' 组件目录
├── assets              ' 静态资源目录
├── environments        ' 环境配置目录
├── favicon.ico         ' 网站图标
├── index.html          ' 主页面文件
├── main.ts             ' 网站的执行入口
├── polyfills.ts        ' 标准差异弥补配置
├── styles.css          ' 全局风格文件
├── test.ts             ' 测试入口
├── tsconfig.app.json   ' TypeScript配置
├── tsconfig.spec.json  ' TypeScript配置
└── typings.d.ts        ' 类型定义文件
```
---
架构
===

<p style="text-align:center"><img src="./images/angular2/overview2.png"/>
</p>

---
模块(Module)
===

Angular是基于模块组织的，并且有自己的模块化组件：`NgModule`
每个Angular应用都至少有一个`NgModule`的类作为根模块(Module)。

`NgModule`是一个修饰性函数，它的参数是一个元对象。基于这个元对象的属性，来描述这个模块。

它有几个重要的属性。

---
重要的属性
===
`declarations` - 所有属于这个模块的视图类。
	Angular有三种视图类：
    1. 组件（component）
    2. 指令(directive)
    3. 管道（pipe）
`exports` - 可以导出为其它模块所用的各种声明。
`imports` - 从其它模块里引入的类。
`providers` - 服务的创建者
`bootstrap` - 主应用的视图。

---
my-app的Module代码：

```
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
---
启动应用
===
启动这个根模块就可以启动Angular应用。
通常在在开发期是通过启动`main.ts`实现的。
```
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { AppModule } from './app/app.module';

platformBrowserDynamic().bootstrapModule(AppModule);
```
---
组件(Component)
===
一个组件是指控制着一块叫做视图的屏幕。

一个组件的逻辑定义在一个类里。这个类通过它的APP与这个视图交互。

Angular会根据用户的行为创建，更新，销毁这些组件。

---
模板(Template)
===
组件(Component)的视图(view)是通过其相应的模板(template)来实现的。

模板采用了一定的模板语法来实现。

```
<h2>Hero List</h2>
<p><i>Pick a hero from the list</i></p>
<ul>
  <li *ngFor="let hero of heroes" (click)="selectHero(hero)">
    {{hero.name}}
  </li>
</ul>

<hero-detail *ngIf="selectedHero" [hero]="selectedHero"></hero-detail>
```
---


<p style="text-align:center"><img src="./images/angular2/component-tree.png" style="height:600px;width:800px"/>
</p>

---

元数据（Metadata）
===
元数据用于告诉Angular如何处理一个类。

默认在Angular里，组件就是一个类。

直到你使用了TypeScript的装饰符修饰了这个类。

比如：
```
@Component({
  selector:    'hero-list',
  templateUrl: './hero-list.component.html',
  providers:  [ HeroService ]
})
```
---
这里的`@Component`就是一个修饰器(decorator)。
它会将直接跟在他后面的类解析成是组件类。

同时有几个重要的参数选项：

1. `selector`
CSS选择器，告诉Angular创建或者插入一个组件实例，在HTML页面里表现一个标签，如这里的`hero-list`。

2. `templateUrl`
组件对应的模板地址。

3. `providers`
一系列组件需要的依赖注入的服务提供者。这是告诉Angular这个组件的构建器需要HeroService这样的服务提供者。

---
数据绑定
===
支持四种形式：

<p style="text-align:center"><img src="./images/angular2/databinding.png"
style="height:400px;width:600px"/>
</p>

---
值绑定：
```
<li>{{hero.name}}</li>
```
属性绑定：
```
<hero-detail [hero]="selectedHero"></hero-detail>
```
事件绑定：
```
<li (click)="selectHero(hero)"></li>
```
双向绑定（表单绑定）：

```
<input [(ngModel)]="hero.name"/>
```
---
指示符（Directives）
===
Angular的模板是动态的。当Angular对模板进行渲染时。Angular会根据模板的指示符将相应的内容转化成DOM。

一个指示符就是一个带有`@Directive`修饰符的类。

一个组件实际上是一个带有模板的指标符。

> 虽然组件其实就是指示符。但是组件与指示符有很多不同的涵义，并且组件对于Angular来说非常核心，因此将他们分开讨论。

---
指示符类型
===
1. 模板指示符：即组件
2. 结构化指示符：通常用于增加相同类型的元素
```
<li *ngFor="let hero of heroes"></li>
```
3. 属性指示符： 改变展现与行为

```
<hero-detail *ngIf="selectedHero"></hero-detail>
```
---
服务（Services）
===

服务是一种非常广泛的分类，这可以包括任何值，函数或者属性，只要你的应用使用得到。

几乎所有的事情都可能成为一种服务。

在Angular里，服务是一个特定目的类。它目录是做一种特定的事情并且做好。

示例：
日志服务、数据服务， 消息服务， 应用配置服务等等。

---
服务
===
Angular没有任何地服务的限制。没有服务的基类，也没有服务的指示符,也不需要注册。
但是服务对Angular仍非常重要，几乎每个组件都会使用到服务。

---

依赖注入（Dependency injection）
===
依赖注入是一个开发模式。它让类接收依赖的类，而不是自己创建类。
Angular的构建器里就用来接收各种依赖注入的类。

依赖注入的好处是：
可以灵活接收各种不同的扩展类，只要核心API不变，类实际可以随意的变化。

---





























