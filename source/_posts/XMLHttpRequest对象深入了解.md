---
title: XMLHttpRequest对象深入了解
date: 2018/12/1 14:42:31
categories: Ajax与Comet
---

> ###### IE7之前的版本不支持原生***XHR***对象

IE7之前的版本的XHR对象是通过MSXML库中的一个ActiveX对象实现的，这个MSXML库包括***MSXML2.XMLHttp，MSXML2.XMLHttp.3.0，MSXML2.XMLHttp.6.0***。

IE7之前的版本创建XHR，实现函数如下：

```javascript
function creatXHR(){
    if(typeof arguments.callee.activeXString != 'string'){
        var versions = ['MSXML2.XMLHttp.6.0','MSXML2.XMLHttp.3.0','MSXML2.XMLHttp'],
            i,len;
        for(i=0; len<versions.length; i<len; i++){
            try{ //从最高版本开始创建，如果创建失败就catch，跳过，继续循环直到结束。
                new ActiveXObject(versions[i]);
                arguments.callee.activeXString = versions[i];
                break;
            }catch(ex){
                //跳过
            }
        }
       
       }
    return new ActiveXObject(arguments.callee.activeXString);
}
```

> ###### IE7+，Firefox，Opera，Chrome，Safari。

以上的所有浏览器都支持原生的XHR对象，创建XHR对象如下：

```javascript
ver XHR = new XMLHttpRequest();
```

> ###### 封装公用函数。

```javascript
function createXHR(){
    if(typeof XMLHttpRequest != 'undefined'){ //浏览器支持XMLHttpRwquest对象
        return new XMLHttpRequest();
    }else if(typeof ActiveXObject != 'undefined'){ //IE7以下，拥有ActiveXObject对象
        if(typeof arguments.callee.activeXString != 'string'){
            var versions = ['MSXML2.XMLHttp.6.0','MSXML2.XMLHttp.3.0','MSXML2.XMLHttp'],
                i,len;
            for(i=0; len<versions.length; i<len; i++){
                try{
                    new ActiveXObject(versions[i]);
                    arguments.callee.activeXString = versions[i];
                    break;
                }catch{
                    //跳过
                }
            }
        }；
        return new ActiveXObject(arguments.callee.activeXString);
    }else{ //所有对象都不存在
        throw new Error("No XHR object available.")
    }
}；

var XHR = createXHR();
```

