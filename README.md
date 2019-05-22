# 柳叶清单

![list](http://upload-images.jianshu.io/upload_images/588640-fa6dc005e8614404.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

[柳叶清单](http://gudong.name/list)是自己独立开发设计的一个 Web 清单应用，目前网页版已经上线运行，地址如下：

[http://gudong.name/list](http://gudong.name/list)

开发初衷：[柳叶清单：管理日程的网页清单程序](https://gudong.name/2018/06/09/list-evety-day.html)

于此同时，为了方便其他开发者使用清单服务，现在开放了部分 API，**以便大家开发自己的 Todo 应用或者 demo 小程序**。

如果使用中有任何问题，也可以在 [issue](https://github.com/maoruibin/liuye/issue) 中进行反馈。

## 关于作者
* Android 工程师，[咕咚翻译](https://sspai.com/post/33226)等多款 APP 应用作者。
* 微博：[大侠咕咚](http://weibo.com/maoruibin)
* 个人主页：[咕咚](https://gudong.name/)


## API model 关系说明

为了对清单 API 有更好的认识，这里先简单说一下具体的数据 model 关系，目前一共有 4 个 model，分别是 User、Project、Group、Todo.

* User: 用户信息
* Project：清单项目，一个用户（User）可以创建多个清单项目。
* Group：分组，一个清单项目（Project）包含多个清单分组
* Todo：事项，每个分组（Group）下有若干 Todo 组成

这个关系用图表示出来如下所示：

![](https://ws3.sinaimg.cn/large/006tNbRwly1fv2i1id2gtj316m0heaa9.jpg)

上面的示意有点抽象，这里用一个具体的例子进行展示如下：

![](https://ws1.sinaimg.cn/large/006tNbRwly1fv2i15reybj31cw0ok3z8.jpg)

下面是目前开放出来的所有数据操作相关的 API，包括用户登录、注册，以及事项（Todo）、分组（Group）、项目（Project）数据的操作，如下所示：

-----

## 用户信息

### 登录
```
https://waishuo.leanapp.cn/api/v1.0/users/login
```

请求方式：POST 

请求参数：

![](https://ws3.sinaimg.cn/large/0069RVTdly1fv122pzfs4j30np02na9x.jpg)

响应结果：
![](https://ws1.sinaimg.cn/large/006tNbRwly1fv249o3de2j31dw0pu0uv.jpg)

### 注册
```
https://waishuo.leanapp.cn/api/v1.0/users/register
```

请求方式：POST 

请求参数：
![](https://ws1.sinaimg.cn/large/0069RVTdly1fv125ajg0ij30nu03ia9z.jpg)

响应结果：
![](https://ws1.sinaimg.cn/large/006tNbRwly1fv24kj4l6nj31do0ouwgj.jpg)

### 获取用户信息
```
https://waishuo.leanapp.cn/api/v1.0/users/<userId>
```

请求方式：GET 

>  说明：url 请求参数中最后需要指定 user id

请求参数：

无


响应结果：
![](https://ws4.sinaimg.cn/large/006tNbRwly1fv24s4zezxj31di0fgjsg.jpg)

-----
## Todo 

### 创建 todo
```
https://waishuo.leanapp.cn/api/v1.0/todos
```

请求方式：POST 

请求参数：

![](https://ws4.sinaimg.cn/large/006tNbRwly1fv2gqi0bulj31bc0damxw.jpg)

响应结果：

![](https://ws2.sinaimg.cn/large/006tNbRwly1fv2abvicb4j31e00icjsm.jpg)


### 更新 Todo
```
https://waishuo.leanapp.cn/api/v1.0/todos/\<todoId\>
```

请求方式：PUT

> 说明：url 请求参数中最后需要指定 todo id

请求参数：

![](https://ws1.sinaimg.cn/large/006tNbRwly1fv2gw0uml2j31bi0eymy1.jpg)

响应结果：

![](https://ws3.sinaimg.cn/large/006tNbRwly1fv2acucb8xj31e00f2gma.jpg)


### 删除 Todo
```
https://waishuo.leanapp.cn/api/v1.0/todos/<todoId>
```

请求方式：DEL 

请求参数：

> 说明：url 请求参数中最后需要指定 todo id

响应结果：

![](https://ws2.sinaimg.cn/large/006tNbRwly1fv2adkk67pj31ec05sweh.jpg)

### 获取 Todo
```
https://waishuo.leanapp.cn/api/v1.0/todos/<todoId>
```

请求方式：GET 

请求参数：

> 说明：url 请求参数中最后需要指定 todo id

响应结果：

![](https://ws2.sinaimg.cn/large/006tNbRwly1fv2aemqnszj31ea0hqwfp.jpg)


-----

## 分组 API

### 创建分组
```
https://waishuo.leanapp.cn/api/v1.0/groups
```

请求方式：POST 

请求参数：

![](https://ws4.sinaimg.cn/large/006tNbRwly1fv2atskz8rj31bc0aiwev.jpg)

响应结果：

![](https://ws2.sinaimg.cn/large/006tNbRwly1fv2au53o3dj31e00d6js3.jpg)


### 更新分组
```
https://waishuo.leanapp.cn/api/v1.0/groups/<groupId>
```

请求方式：PUT

> 说明：url 请求参数中最后需要指定 groupId

请求参数：

![](https://ws1.sinaimg.cn/large/006tNbRwly1fv2awsuikvj31ba0akaaf.jpg)

响应结果：

![](https://ws3.sinaimg.cn/large/006tNbRwly1fv2ax5naqij31e80eeaax.jpg)

### 获取项目分组列表
```
https://waishuo.leanapp.cn/api/v1.0/groups/projects/<projectId>
```

请求方式：GET

请求参数：

> 说明：url 请求参数中最后需要指定 projectId

响应结果：

![](https://ws3.sinaimg.cn/large/006tNbRwly1fv2b730zvqj31dm0g8t9n.jpg)


### 删除分组
```
https://waishuo.leanapp.cn/api/v1.0/groups/<groupId>
```

请求方式：DEL 

请求参数：

> 说明：url 请求参数中最后需要指定 groupId

响应结果：

![](https://ws1.sinaimg.cn/large/006tNbRwly1fv2axmd09bj31e005m3yi.jpg)

-----

## Project 相关 api

### 创建项目
```
https://waishuo.leanapp.cn/api/v1.0/project
```

请求方式：POST

请求参数：

![](https://ws2.sinaimg.cn/large/006tNbRwly1fv23m9qfscj31bm06s0sx.jpg)

响应结果：

![](https://ws1.sinaimg.cn/large/006tNbRwly1fv23lkafkcj31dk0c60te.jpg)

### 编辑项目
```
https://waishuo.leanapp.cn/api/v1.0/project
```

请求方式：PUT

请求参数：

![](https://ws3.sinaimg.cn/large/006tNbRwly1fv2bfvigu6j31bk07y3yp.jpg)

响应结果：

![](https://ws1.sinaimg.cn/large/006tNbRwly1fv2bgplan5j31e20eawfd.jpg)

### 删除项目
```
https://waishuo.leanapp.cn/api/v1.0/projects/<projectId>
```

> 注意：删除时，会把项目下的分组以及 todo 全部删除

请求方式：DEL 

> 说明：url 请求参数中最后需要指定 projectId


