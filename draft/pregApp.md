
* 20160129 打算以全栈的方式做一个app，由于不想陷入回调地狱，打算以koa为服务端底层框架。
* 20160130 koa的hello world很好写，目前在探索如何跟模板结合在一起。应该直接选型react 服务端渲染。
* 20160201 react server render 和jade这些不同，直接用renderToString就ok了。
* 20160202 加上redux router等的服务端渲染比较麻烦，社区比较混乱，没有统一的对应的说明。先做传统的客户端，再做接口，再考虑服务端渲染。
* 20160203 今天主要是加了nodemon实时监控，服务端还要加上websocket。
* 20160204 实现了客户端ws提交数据到服务端，然后服务端识别并且存到数据库
* 20160215 节后第一天，主要看了async await和genetor的区别联系，规划一下聊天功能的流程
* 20160216 在自己的代码里面加入了html5+的功能，很轻易调用原声摄像头。整理了一下ui流程，确认前端用weui。
* 20160217 后面以业务为主，有特殊处理再记录
* 20160228 基本理解了koa的中间件机制，所有操作都做成中间件，通过虚拟上下文做变量传递。客户突然说不用mysql而是用mssql，为稳妥起见还是用orm之类的访问数据库。
* 20160406 要找一个一对一聊天的例子，观察其中的数据流向。
* 20160407 找了几个例子，最终还是觉得socket.io官网最靠谱。socket的基本原则是，一个服务端对应多个客户端。客户端的消息要经过服务端中转，所以客户端emit,on的对象都是服务端。而服务端on事件，所有的客户端都能触发，但是emit的时候，就需要区分客户端进行处理了。
```
io.on('connection', function(socket){
  //这里，io是公共的，整个服务器的
	//socket则是具体连接的那个客户端的
	io.to(roomid).emit( ) //服务端只往那个房间发送消息
});
```
* 20160410 理解了socket的原理之后，程序逻辑清晰，可以跑了，虽然很多bug。发现打包到手机用file协议也是可以用websocket进行通讯的。有空研究源代码。
* 20160414 处理了聊天消息显示的部分，感觉到IM软件跟以前做的CRM-like系统的数据处理差别
