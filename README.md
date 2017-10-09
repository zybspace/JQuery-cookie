# JQuery-cookie
onload是页面加载，onbeforeunload监听浏览器关闭。所以当页面关闭的时候触发的事件需调用onbeforeunload。 而清空页面cookie的jquery代码如下：
    var cookies = $.cookie(); 
    for (var cookie in cookies) { 
      $.removeCookie(cookie); 
    }
另外，onbeforeunload事件监听： 
　　说明：目前三大主流浏览器中firefox和IE都支持onbeforeunload事件,opera尚未支持。 
　　用法： 
　　　object.onbeforeunload = handler 
　　　<element onbeforeunload = “handler” … ></element> 
　　描述： 
　　　事件触发的时候弹出一个有确定和取消的对话框，确定则离开页面，取消则继续待在本页。handler可以设一个返回值作为该对话框的显示文本。 

　　触发于： 
　　　1·关闭浏览器窗口 
　　　2·通过地址栏或收藏夹前往其他页面的时候 
　　　3·点击返回，前进，刷新，主页其中一个的时候 
　　　4·点击 一个前往其他页面的url连接的时候 
　　　5·调用以下任意一个事件的时候：click，document write，document open，document close，window close ，window navigate ，window NavigateAndFind,location replace,location reload,form submit. 
　　　6·当用window open打开一个页面，并把本页的window的名字传给要打开的页面的时候。 
　　　7·重新赋予location.href的值的时候。 
　　　8·通过input type=”submit”按钮提交一个具有指定action的表单的时候。 
　　可以用在以下元素： 
　　　BODY, FRAMESET, window 
　　平台支持： 
　　　IE4+/Win, Mozilla 1.7a+, Netscape 7.2+, Firefox0.9+ 
jsp代码示例1：
  <head>   
  <meta http-equiv="Content-Type" content="text/html; charset=gb2312" />   
  <title>onbeforeunload测试</title>   
  <script>   
    function checkLeave(){   
　   event.returnValue="确定离开当前页面吗？";   
    }   
  </script>   
  </head>   
  <body onbeforeunload="checkLeave()">   
  </body>   
  </html>
  
jsp代码示例2：
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">  
<HTML>  
 <HEAD>  
  <TITLE> top.html </TITLE>  
 </HEAD>  
 <script language="JavaScript">  
    window.onbeforeunload = function()  
    {  
        //  这是用来设定一个时间, 时间到了, 就会执行一个指定的 method。  
        setTimeout(onunloadcancel, 10);  
        return "真的离开?";  
    }  
    window.onunloadcancel = function()  
    {  
        alert("取消离开");  
    }  
</script>  
   
<BODY>  
   <p> 点击关闭按钮  监听</p>  
</BODY>  
</HTML>

另外，在此拓展一个判断页面是否真的关闭和刷新的方法：
window.onbeforeunload=function (){   
    alert("===onbeforeunload===");   
  if(event.clientX>document.body.clientWidth && event.clientY < 0 || event.altKey){   
    alert("你关闭了浏览器");   
  }else{   
    alert("你正在刷新页面");   
  }   
}   
