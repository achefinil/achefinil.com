---
title: "js-Ajax"
date: 2015-10-26T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---

> 最近为了减少页面加载文件大小，省去了jQuery包。直接使用原生js码了Ajax。

```
/**
 * @函数说明 Ajax封装
 * @修改历史
 *      2015-09-18  Achefinil   重写ajax
 */
function AjaxClass(){
    var XmlHttp = false;
    try  {
        XmlHttp = new XMLHttpRequest();//FireFox专有
    } catch(e) {
        try {
            XmlHttp = new ActiveXObject("MSXML2.XMLHTTP");
        } catch(e2) {
            try {
                XmlHttp = new ActiveXObject("Microsoft.XMLHTTP");
            } catch(e3) {
                showMsg("请使用现代浏览器");
                XmlHttp = false;
            }
        }
     }
    var me = this;
    this.Method = "POST";
    this.Url = "";
    this.Async = true;
    this.param = "";
    this.CallBack = function(){};
    this.Loading = function(){};
    this.Send = function(){
        if (this.Url==""){
            return false;
        }
        if (!XmlHttp){
            return IframePost();
        }
        XmlHttp.open (this.Method, this.Url, this.Async);
        if (this.Method=="POST"){
            XmlHttp.setRequestHeader("Content-Type","application/x-www-form-urlencoded");
        }
        XmlHttp.onreadystatechange = function(){
            if (XmlHttp.readyState == 4){
                var Result = false;
                if (XmlHttp.status == 200){
                    Result = XmlHttp.responseText;
                }else{
                    if(XmlHttp.status == 0){
                        showMsg("网络异常，请检查您的网络");
                    }else{
                        showMsg("登陆失败，请稍后重试");
                    }
                    return;
                }
                XmlHttp = null;
                me.CallBack(Result);
            }else{
                me.Loading();
            }
        };

        if (this.Method=="POST"){
            XmlHttp.send(this.param);
        } else {
            XmlHttp.send(null);
        }
    };

    //Iframe方式提交
    function IframePost(){
        var Num = 0;
        var obj = document.createElement("iframe");
        obj.attachEvent("onload",function(){
            me.CallBack(obj.contentWindow.document.body.innerHTML);
            obj.removeNode();
        });
        obj.attachEvent("onreadystatechange",function(){ if (Num>=5) {showMsg(false);obj.removeNode();} });
        obj.src = me.Url;
        obj.style.display = 'none';
        document.body.appendChild(obj);
    }
}
```

> 调用方法

```
//调用ajax
var Ajax = new AjaxClass();// 创建AJAX对象
Ajax.Method = "POST";// 设置请求方式为POST
Ajax.Url = // URL
Ajax.Async = true;// 是否异步
Ajax.param = // 参数
Ajax.Loading = function(){  //等待函数
    //  document.write("loading...");
};

Ajax.CallBack = function(response) {
    // 回调函数 ...
};
Ajax.Send();
```