# ionic-safe-usedemo
Android 安卓安全插件,禁止截屏、获取签名证书SHA1、获取安装包SHA1、检测是否Root
## IonicSafe用途
- 禁止截屏，登录页面禁止app截屏防止恶意程序盗取登录密码
- 应用签名检测，防止APP被二次打包
- 应用完整性校验，验证APK文件是否被修改或者删除
- 检测是否Root，确保应用在相对安全的环境中运行
- 检测是否调试调试模式运行
- 检测进程是否被追踪
- 检测是否模拟器运行
- 检测是否有wifi代理
- 动态调试检测

## IonicSafe使用说明

#### 引入插件

```javascript
var safeModule = uni.requireNativePlugin("Ionic-Safe");
```

### 禁止截屏

```javascript
safeModule.isDisableScreen(1, ret => {
    //返回值 
    //ret.state true/false	
    console.log(ret);
});
```

### 允许截屏

```javascript
safeModule.isDisableScreen(0, ret => {
     //返回值 
    //ret.state true/false	
    console.log(ret);
});
```


### 获取签名文件SHA1

```javascript
safeModule.getSignature(ret => {
     //返回值 
    //ret.data SHA1
    //ret.state true/false	
	console.log(ret);
});
```

### 获取APK包SHA1

```javascript
safeModule.getApkSHA(ret => {
    //返回值 
    //ret.data SHA1
    //ret.state true/false	 
	console.log(ret);			
});
```

### 检查是否Root

```javascript
safeModule.checkIsRoot(ret => {
	//返回值 true/false			
});
```
### 检查是否调试模式

```javascript
safeModule.isDebuggable(ret => {
	//返回值 true/false			
});
```
### 检查进程是否被追踪

```javascript
safeModule.isUnderTraced(ret => {
	//返回值 true/false			
});
```
### 检查是否是模拟器运行

```javascript
safeModule.isEmulator(ret => {
	//返回值 true/false			
});
```
### 检查是否是有wifi代理

```javascript
safeModule.isWifiProxy(ret => {
	//返回值 true/false			
});
```
### 检查动态调试（无返回值，存在就会退出应用，定时配合 isUnderTraced 使用效果更佳）

```javascript
safeModule.detectedDynamicDebug();
```
### 使用Demo
[点击跳转](https://github.com/zerox-v/ionic-safe-usedemo.git)
