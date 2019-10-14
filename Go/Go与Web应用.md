[TOC]

#   使用Go语言构建Web应用
*   可扩展Web应用
    *   垂直扩展：并发编程支持，goroutine
    *   水平扩展：多个Go Web应用之上架设代理
*   模块化Web应用
    *   Go的接口机制可以实现动态类型匹配，空接口，函数类型，使用函数作为值以及闭包，Go也常用于创建微服务
*   可维护Web应用
    *   Go拥有灵活的包管理系统，还有一整套优秀的工具，如源代码格式化成程序gofmt，文档工具godoc等，还内置了对测试的支持：gotest，web应用测试工具
*   高性能Web应用
    *   提供接近于C语言的性能，Go程序会被编译为本地代码，运行得比解释型语言更快，goroutine使得Go应用可以同时处理多个请求

#   Web应用的工作原理
*   HTTP请求
    *   HTTP请求由一系列文本行组成，按照以下顺序进行排列：
        *   请求行
        *   零个或任意多个请求首部
        *   一个空行
        *   可选的报文主体
    *   请求方法：GET,HEAD,POST,PUT,DELETE,TRACE,OPTIONS,CONNECT,PATCH
    *   安全的请求方法：只要求服务器提供信息不会对服务器得状态做任何修改就是安全的方法，如GET,HEAD,OPTIONS,TRACE，除此之外得方法都是不安全的
    *   幂等的请求方法：PUT和DELETE
    *   请求首部
        *   Accept
        *   Accept-Charset
        *   Authorization
        *   Cookie
        *   Content-Length
        *   Content-Type
        *   Host
        *   Referrer
        *   User-Agent
*   HTTP响应
    *   跟HTTP请求一样，HTTP响应也是由一系列文本行组成的：
        *   一个状态行，包含状态码和响应的原因短语
        *   零个或任意数量的响应首部
        *   一个空行
        *   一个可选的报文主体
    *   响应状态码
        *   1XX 情报状态码
        *   2XX 成功状态码
        *   3XX 重定向状态码
        *   4XX 客户端错误状态码
        *   5XX 服务器错误状态码
    *   响应首部
        *   Allow
        *   Content-Length
        *   Content-Type
        *   Date
        *   Location
        *   Server
        *   Set-Cookie
        *   WWW-Authenticate
*   URI
    *   URI(统一资源标识符)包含了URN(统一资源名称)和URL(统一资源定位符)
    *   一般格式：<方案名称>:<分层部分>[? <查询参数>][# <片段>]
*   Web应用的各个组成部分
    *   通过HTTP协议，以HTTP请求报文的形式获取客户端输入；
    *   对HTTP请求报文进行处理，并执行必要的操作；
    *   生成HTML，并以HTTP响应报文的形式将其返回给客户端。
    *   为了完成这些任务，Web应用被分成了**处理器**和**模板引擎**两个部分。
    *   **处理器**
    
    *   **模板引擎**
