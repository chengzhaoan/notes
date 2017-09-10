# 前言
 最近一段时间学习了基础一些web的基础知识，感觉以前一些闹不清楚的额东西还是很重要的，尤其对于知识的全面理解，起码应当知道大致的来龙去脉。
 ## http协议
    
   [http协议介绍1](http://www.cnblogs.com/ranyonsue/p/5984001.html/)<br>
   [http协议介绍2](http://www.cnblogs.com/li0803/archive/2008/11/03/1324746.html)
    
#### request
```
GET /562f25980001b1b106000338.jpg HTTP/1.1
Host    img.mukewang.com
User-Agent    Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.106 Safari/537.36
Accept    image/webp,image/*,*/*;q=0.8
Referer    http://www.imooc.com/
Accept-Encoding    gzip, deflate, sdch
Accept-Language    zh-CN,zh;q=0.8
```
1 请求行         请求的类型 资源   协议</br>
2 请求头部       目的地址 </br>
  在post请求中关系到spring的解析工作的是的行为
  Content-Type:application/x-www-form-urlencoded 
  xml json 等等
  
   
```
    text/html ： HTML格式
    text/plain ：纯文本格式      
    text/xml ：  XML格式
    image/gif ：gif图片格式    
    image/jpeg ：jpg图片格式 
    image/png：png图片格式
   以application开头的媒体格式类型：
```


```
   application/xhtml+xml ：XHTML格式
   application/xml     ： XML数据格式
   application/atom+xml  ：Atom XML聚合格式    
   application/json    ： JSON数据格式
   application/pdf       ：pdf格式  
   application/msword  ： Word文档格式
   application/octet-stream ： 二进制流数据（如常见的文件下载）
   application/x-www-form-urlencoded ：
   multipart/form-data ： 需要在表单中进行文件上传时，就需要使用该格式
```

[spring mcv 和content-type的关系](http://blog.csdn.net/blueheart20/article/details/45174399)<br>
    @ResponseBody   隐含的使用request传入content-type的类型
    
    以上的目前常用的就是json，responsebody 就是不将返回值按照映射解析为路径地址的意思
#### http 的返回码
    respond 状态行
```
    HTTP/1.1 200 OK      
```
