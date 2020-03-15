# Mirsh.Payment
微信支付v3 API

##一、基本信息
地址：https://github.com/gitmirsh/Mirsh.Payment  
代码搭建环境：  
1.win10   
2.vs2012(.net framework4)  
3.git  

##二、解决方案
包含两个项目  
1.Mirsh.Payment               --WXPay API v2/v3底层实现  
2.Mirsh.Payment.UnitTest      --测试单元，用于功能测试  
  
需注意Mirsh.Payment 依赖一下组件  
/lib/Mirsh.dll                 --主要用到httpclient  
/lib/BouncyCastle.Crypto.dll   -- 解密数据使用  
/lib/Newtonsoft.Json.dll       --json序列化与反序列化  
  
##三、使用示例
```csharp
var api = new WXV3Api()
{
    CertFilePath = "微信商户证书路径",
    MerchantId = "证书对应的商户号"
};

// Get方式调用,返回Json字符串
var result = api.Get("/v3/certificates" /*可以相对路径，也可以全路径*/, null/*参数，字典类型*/);

// Get方式调用,如果有定义返回类型，可以调用此泛型方法
var resultT = api.Get<PlatformCertificatesResponse>("/v3/certificates" /*可以相对路径，也可以全路径*/, null/*参数，字典类型*/);

// POST方式调用,返回Json字符串
result = api.Post("资源路径" /*可以相对路径，也可以全路径*/, "{}"/*参数，请求体json字符串*/);

// Get方式调用,如果有定义返回类型，可以调用此泛型方法
resultT = api.Post<PlatformCertificatesResponse>("资源路径" /*可以相对路径，也可以全路径*/, "{}"/*参数，请求体json字符串*/
```
