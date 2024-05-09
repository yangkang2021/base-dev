# web跨域解决方案
> 如果目标资源的服务不能配置，就只能代理，其他方式要改页面搞乱页面。

## 一. 什么是跨域？
跨域就是当在页面上发送ajax请求时，由于浏览器同源策略的限制，要求当前页面和服务端必须同源，也就是协议、域名和端口号必须一致。
![](.images/b45121d4.png)

## 二. 解决方案
1. CORS：目标资源服务指定可以谁访问
3. 搭建Node代理服务器
4. Nginx反向代理
5. JSONP
5. postMessage 
6. Websocket
https://blog.csdn.net/m0_37873510/article/details/126558023

## 三. iris跨域解决
>处理Options请求和返回Access-Control-Allow-Origin
```
1. 编写中间件，将允许跨域的header添加到响应头
//Cors
funcCors(ctxiris.Context){
    ctx.Header("Access-Control-Allow-Origin","*")
    //ctx.Header("Access-Control-Allow-Headers","DNT,X-Mx-ReqToken,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Authorization")
    //ctx.Header("Access-Control-Allow-Methods","GET,POST,OPTIONS,HEAD,DELETE")
    ifctx.Method()=="OPTIONS"{
        ctx.Header("Access-Control-Allow-Methods","GET,POST,PUT,DELETE,PATCH,OPTIONS")
        ctx.Header("Access-Control-Allow-Headers","Content-Type,Accept,Authorization")
        ctx.StatusCode(204)
        return
    }
    ctx.Next()
}

func main(){
    app:=iris.New()
    app.Use(recover.New())
    // 所有请求前面添加拦截器
    app.Use(Cors)
     // 如果API接口没有实现OPTIONS方法，需要给所有接口设置缺省的OPTIONS方法，不然捕捉不到对应API接口的OPTIONS请求。
    common:=app.Party("/")
    {
        common.Options("*",func(ctxiris.Context){
            ctx.Next()
        })
    }

    api:=app.Party("/api")
    api.Get("/index",IndexHandler)
    app.Run(iris.Addr("0.0.0.0:8080"))
}
```


