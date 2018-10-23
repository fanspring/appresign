# appresign


代码源于[AppResign](https://github.com/Urinx/iOSAppHook/tree/master/AppResign)，主要基于此做了如下修改：

### 使用证书ID来签名
考虑到使用自己免费apple id的临时证书时，mac机上会存在多个名称相同的证书，如果仍然使用名称来code resign则会报错如下

```
ambiguous (matches "iPhone Developer: *********@qq.com (LZ7VN9FRTQ)" and "iPhone Developer: *********@qq.com (LZ7VN9FRTQ)" in /Users/***/Library/Keychains/login.keychain-db)
```

此时应该使用对应的证书ID来签名。


### 显示provision文件支持的device名称 
当手机通过usb连接mac电脑时，对于每个provision文件，会显示出它所支持的设备名称，从而便于你选择使用哪个provision文件来签名，避免签名了无法安装在该手机上。


### 过滤CSSMERR_TP_CERT_REVOKED的证书

使用自己apple id的免费证书，多次使用后会存在CSSMERR_TP_CERT_REVOKED的证书，签名时将其过滤

