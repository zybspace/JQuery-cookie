# JQuery-cookie
onload是页面加载，unload是页面关闭。所以当页面关闭的时候触发的事件需调用unload。 而清空页面cookie的jquery代码如下： var cookies = $.cookie(); for (var cookie in cookies) { $.removeCookie(cookie); }
