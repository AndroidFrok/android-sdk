 # Upyun Android SDK

 ## 演示代码

```
UploadManager.getInstance().upload(new File(localFilePath), paramsMap, KEY, completeListener, progressListener);

UploadManager.getInstance().upload(new File(localFilePath), paramsMap, signatureListener, completeListener, progressListener);

```

参数说明：

* localFilePath	文件路径
* paramsMap	参数键值对
* KEY	表单 API 验证密钥（form_api_secret）
* signatureListener 获取签名回调
* completeListener	结束回调
* progressListener 进度条回调

两种上传方式可根据自己情况选择一种，KEY用户可直接保存在客户端，signatureListener 用户可以通过请求服务器获取签名返回客户端。signatureListener回调接口规则如下：

```
        SignatureListener signatureListener=new SignatureListener() {
            @Override
            public String getSignature(String raw) {
                return UpYunUtils.md5(raw+KEY);
            }
        };
        
```
将参数raw 传给后台服务器和表单密匙连接后做一次md5运算返回结果。
参数键值对中Params.BUCKET（上传空间名）和Params.SAVE_KEY（保存路径）为必选参数，其他可选参数见Params或者[官网API文档](http://docs.upyun.com/api/form_api/)

其他详情见APP module 下的[MainActivity](http://gitlab.widget-inc.com/upyun-sdk/android-sdk/blob/master/app/src/main/java/com/upyun/sdktest/MainActivity.java)。

 ## 使用说明：
 1.直接下载JAR包复制进项目使用。
 
 2.sdk已经上传JCenter，android studio的用户可以直接在gradle中添加一条dependencies使用
 
 ```
 compile 'com.upyun:library:1.0.1'
 ```
 
 ## 配置说明
	在UpConfig中可以对sdk的一些参数进行配置，
 ## 运行环境
 android 2.3（API10） 以上环境
 
 ## 代码许可
Licenses [Apache-2.0](http://opensource.org/licenses/apache2.0.php) 