LaunchAppFromWebPage
====================

Launch an android app by js 


在手机浏览器上，点击下载app的按钮时，实现如果已经安装了本app就直接打开，未安装就下载。

实现原理：
  1、  给指定的activity添加一个intent-filter，like this
  <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <action android:name="android.intent.action.VIEW" />

                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />

                <data
                    android:host="com.example.urltest"
                    android:scheme="demo" />
            </intent-filter>
            
  2、在js代码中，按钮响应部分，添加settimeout，如果没有安装，加载demo://com.example.urltest会有一个超时错误，而
  settimeout就是用来替补404错误
  setTimeout() 方法用于在指定的毫秒数后调用函数或计算表达式。
  
function launchAndroidApp()
{
window.location.href='demo://com.example.urltest';
setTimeout(function(){ window.location.href="http://www.baidu.com" }, 3000);
}
