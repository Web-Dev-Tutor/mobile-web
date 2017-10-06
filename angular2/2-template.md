<!-- 

$theme: gaia
template: gaia

-->
模板与数据绑定
===
---

数据显示
===

Angular可以让模板的控件与你的组件属性绑定。

#### 通过嵌入的方式显示组件属性
```
@Component({
  selector: 'my-app',
  template: `
    <h1>{{title}}</h1>
    <h2>My favorite hero is: {{myHero}}</h2>
    `
})
export class AppComponent {
  title = 'Tour of Heroes';
  myHero = 'Windstorm';
}
```
---

#### 通过指定的标签名，自动创建组件
对于上面的组件，可以这样放在主文件里。
这个时候，组件是由Angular自动创建的。

其中`my-app`标签就是生成组件的标签。

```
<body>
  <my-app>loading...</my-app>
</body>
```
---

内联模板(template inline)和文件模板(template file)
===
组件模板有两种保存方式。

一种是内联的，通过`template`定义；
另一种是文件的，通过`templateUrl`定义。

---
使用\*ngFor显示数组
===
对于组件：
```
export class AppComponent {
  title = 'Heroes';
  heroes = ['Windstorm', 'Bombasto', 'Magneta', 'Tornado'];
}
```
他的模板可以这么写。
```
template: `
  <h1>{{title}}</h1>
  <ul><li *ngFor="let hero of heroes">{{ hero }}</li></ul>
`
```
---
使用\*ngIf控制显示
===

假设需要heroes的长度大于3时再显示一个p标签。

```
<p *ngIf="heroes.length > 3">There are many heroes!</p>
```
---
模板语法
===
1. HTML标签
除了`<script>`标签，其它的所有的标签都是合法的。
2. 但是`<html>`,`<body>`, `<base>`这些标签并没有实际的价值。
3. 通过组件(Components)或者指令（Directives)可以组成新的HTML标签。

---
值的插入（Interpolation ）( {{...}} )（1）
===
之前我们已经见过值的插入了，形式如下：
```
<p>My current hero is {{currentHero.name}}</p>
```
这是最基本的应用。

值的插入还可以应用于属性中，形式如下：

```
<h3>
  {{title}}
  <img src="{{heroImageUrl}}" style="height:30px">
</h3>
```
---
值的插入（Interpolation ）( {{...}} )（2）
===


















