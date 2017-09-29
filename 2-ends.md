<!-- 
$theme: gaia
template: invert
-->

各种端的概念
===

---
<!-- *page_number: true -->
经常讨论的端
===
1. 前端，后端
2. 客户端，服务器端
3. 桌面端

---
基于C/S模式的端分类
===

#### 图解

$$ Ends \left \{
\begin{aligned}
Client \left \{
\begin{aligned}
Generic \ Clients \left \{
\begin{aligned}
Desktop\\
Mobile \ \   
\end{aligned}
\right.\\
Browsers \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ 
\end{aligned}
\right. \\
\\
Server \left \{
\begin{aligned}
Raw \ TCP/UDP \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \\
HTTP/WebSocket\ \ \ \ \ \ \ \ \ \ \ \ \ 
\end{aligned}
\right.
\end{aligned}
\right.
$$

---
基于C/S模式的端分类
===

#### ==*客户端*==
1. 常规客户端（移动/桌面）
2. 浏览器端（移动/桌面）
#### ==*服务器端*== 
1. 常规TCP/UDP服务器
2. Web服务器

---
客户端与服务器端的差别
===
1. 通常一个**客户端**只能服务于一个**用户**
2. 通常一个**服务器端**能服务于多个**客户端**

---
基于B/S模式的端分类
===
$$ Ends \left \{
\begin{aligned}
Frontend(Browser) \left \{
\begin{aligned}
HTML \ \ \ \ \ \ \ \ \ \ \ \ \ \ \\
CSS \ \ \ \  \ \ \ \ \ \ \ \ \ \ \ \ \ \  \\
Javascript \ \ \ \ \ \ \ \ 
\end{aligned}
\right. \\
\\
Backend(Server) \left \{
\begin{aligned}
Web \ Server \ \ \ \ \ \ \ \ \ \ \ \ \\
Database  \ Server \ \ \ \ \\
Cache \ Server \ \ \ \ \ \ \ \ \ \\
etc. \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \  \ \ \ \ 
\end{aligned}
\right.
\end{aligned}
\right.
$$

---
基于B/S模式的端分类
===
通常我们基于B/S将我们的应用环境分成前后端。

1. 前端是HTML+CSS+JS组成的浏览器环境
2. 后端是提供服务的各种服务器

所以我们可以看到：
> 前后端主要是针对B/S架构来说的。

---
我在那个端开发？
===
1. 客户端应用
浏览器，Android/iOS Mobile App, WIN32/Mac OS/Linux Desktop
2. 服务器端
Nginx/Apache, WIN32 Web Server, Mac OS Web Server, Linux Web Server

> 我们可以发现，属于那个端，有时候非常清楚，有时候并没有那么明确的。只有当具体的应用场景出现时，我们才能完全分清楚。

---
实际的端案例
===

1. 浏览器通常无法成为服务器。
2. Apache/Nginx通常是以服务器的姿势出现
3. 当我们在Android手机上开发了FTP功能时，实际上Android是建立了FTP服务器，而Android通常被为是客户端。











