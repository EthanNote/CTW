+++
draft = false
date = 2018-09-21T18:09:31+08:00
title = "XML Http Request"
slug = ""
tags = []
categories = []
+++

### Loading progress

Using 'onprogress' callback

https://www.cnblogs.com/gaohj/p/7017722.html

<pre><ch>

<script src="http://file.leeye.net/jquery.js"></script>  
<script>  

var xhr = createXHR();  
xhr.onload = function(event){  
    if((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304){  
        //alert(xhr.responseText);  
    }else{  
        //alert('Request was unsuccessful: '+ xhr.status);  
    }  
}  

xhr.onprogress = function(event){  
    var progress = '';  
    var divStauts = document.getElementById("status");  
    console.log(event);  
    if(event.lengthComputable){  
        progress = ""+Math.round(100*event.loaded/event.total)+"%";  
        divStauts.innerHTML = "Recevied " + progress + " of " + event.total + "bytes";  
    }  
}  

function createXHR(){  
    var xhr = null;  
    try {  
        // Firefox, Opera 8.0+, Safari，IE7+  
        xhr = new XMLHttpRequest();  
    }  
    catch (e) {  
        // Internet Explorer   
        try {  
            xhr = new ActiveXObject("Msxml2.XMLHTTP");  
        }  
        catch (e) {  
            try {  
                xhr = new ActiveXObject("Microsoft.XMLHTTP");  
            }  
            catch (e) {  
                xhr = null;  
            }  
        }  
    }  
    return xhr;  
} 

function upload(){  
    url = 'http://file.leeye.net/test.jpg'  
    xhr.open('get', url, true);  
    xhr.send(null);  
    $('img').attr('src' , url).show();  
}  

</script>  
<button>up</button>  
<div id="status"></div>  
<img style="display: none;">

</ch></pre>