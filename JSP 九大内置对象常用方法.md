---
title: JSP 九大内置对象常用方法
date: 2018-10-01 18:16:21
tags: 
- JSP
- Java
---

## 1. ``request`` 对象常用方法

``request`` 是来自客户端的请求. 客户端的请求信息封装在 ``request`` 对象中. 以下 ``HttpServletRequest`` 类的实例.

|方法 ( 类型 + 方法名 ) |描述|
|----------------------|----|
|String getParameter(String strTextName)|获取表单提交信息|
|Enumeration getParameterNames()|返回可用参数的枚举|
|String[] getParameterValues(String name)|返回包含参数 name 的所有的数组|
|Enumeration getAttributeNames()|返回所有属性名的属性值|
|Object getAttribute(String name)|返回指定属性的属性值|
|String getCharacterEncoding()|返回字节编码方式|
|String getProtocol()|获取用户使用的协议|
|String getServletPath()|获取用户提交信息的页面|
|String getMethod()|获取客户提交信息的方式|
|BufferReader getHeader()|获取 HTTP 头文件的 accept、accept-encoding 和 Host 的值|
|String getRemoteAddr()|获取客户的 IP 地址|
|String getRemoteHost()|获取客户机的名称|
|String getserverName()|获取服务器的名称|
|int getServerPort()|获取服务器端口号|

## 2. ``resopnse`` 对象常用方法

``resopnse`` 对象代表的是对客户端的相应. 向客户端发送文字时直接使用. 以下是 ``HttpServletResopnse`` 类的实例.

|方法 ( 类型 + 方法名 ) |描述|
|----------------------|----|
|String getCharacterEncoding()|返回响应用的是什么字符编码|
|ServletOutputStream getOutputStream()|返回响应的一个二进制输出流|
|PrintWrite getWrite()|返回可以向客户端输出字符的一个对象|
|void setContentLength(int len)|设置响应头长度|
|void setContentTye(String type)|设置响应的 MIME 类型|
|void sendRedirect(Java.lang.String location)|重新定向客户端的请求|

<!-- more -->
## 3. ``session`` 常用方法

``session`` 指的是客户端与服务器的一次回话, 从客户连接到服务器的一个 WebApplication 开始, 直到客户端与服务器断开连接为止. 它是 ``HttpSession`` 类的实例.

|方法 ( 类型 + 方法名 ) |描述|
|----------------------|---|
|long getCreationTime()|创建 session 创建时间|
|public String getId()|返回 session 创建时JSP引擎为它设置的唯一ID号|
|long getLastAccessedTime()|返回 session 里客户端最近一次请求时间|
|int getMaxInactiveInterval()|返回两次请求间隔多长时间此 session 被取消|
|String[] getValueNames()|返回一个包含此 session 中所有可用属性的数组|
|void invalidate()|取消 session , 使 session 不可用|
|boolean isNew()|返回服务器创建爱你的一个 session , 客户端是否已经加入|
|void removeValue(String name)|删除 session 中指定的属性|
|void setMaxInactiveInterval()| session 被取消 (ms)|


## 4. ``out`` 常用方法
``out`` 对象是 ``JspWriter`` 类的实例, 是向客户端输出内容常用的对象.

|方法 ( 类型 + 方法名 ) |描述|
|----------------------|----|
|void clear()|清除缓冲区的内容|
|void clearBuffer()|清除缓冲区的当前内容|
|void flush()|清空流|
|int getBufferSize()|返回缓冲区以字节数的大小,如果不设置为0|
|int getRemaining()|返回缓冲区还有多少剩余可用|
|bool isAutoFlush()|返回缓冲区满时,是自动清空还是抛出异常|
|void close()|关闭输出流|


## 5. ``page`` 常用方法
``page`` 指当前 ``JSP`` 页面本身, 有点像类中的 ``this`` 指针, 它是 ``java.langlObject`` 类的实例. 「page」对象代表正在运行的由 ``jsp`` 文件产生的类对象.

|方法 ( 类型 + 方法名 ) |描述|
|-----------------------|---|
|class getClass()|返回此 Object 的类|
|int hashCode()|返回此 Object 的 hash 码|
|boolean equals(Object obj)|判断此 Object 是否与指定的 Object 对象相等|
|void copy(Object obj)|把此 Object 拷贝到指定的 Object 对象中|
|Object clone()|克隆此 Object 对象|
|String toString()|把此 Object 对象转换成 String 类的对象|
|void notify()|唤醒一个等待的进程|
|void notifyAll()|唤醒所有等待的进程|
|void wait(int timeout)|使一个进程处于等待直到 timeout 结束或者被唤醒|
|void wait()|使一个线程处于等待直到被唤醒|
|void enterMonitor()|对 Object 进行加锁|
|void exitMonitor()|对 Object 进行开锁|

## 6. ``application`` 常用方法

``application`` 实现了用户间数据的共享, 可存放全局变量. 它开始于服务器的启动, 直到服务器的关闭, 在此期间, 此对象将一直存在; 这样在用户的前后连接或者不同用户之间的连接中, 可以对此对象的同一属性进行操作; 在任何地方对此对象属性的操作, 都将影响到其他对象对此的访问. 服务器的启动和关闭决定了 ``application`` 对象的生命. 它是 ``ServletContest``类的实例.