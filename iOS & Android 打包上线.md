# iOS & Android 打包上线

## iOS打包上传

**1.** 打开`wanke -> General`，修改本次要发布的版本号（图中`3`处）。
**发布到线上**：对于某一个版本（如`3.2.0`），如果要上传`App Store Connect`审核发布到线上的话，每一次上传，`Build`编译版本号（图中`4`处）必须比上一次大，比如第一次上传`3.2.0`版本到`App Store Connect`，比如这次打包的`Build`是`6`, 由于处理失败或者因为项目使用了苹果未允许的`API`，又或者配置错误导致收到苹果的警告⚠️邮件（一般收到警告邮件就要进行处理，否则审核一般都会失败）, 再次处理好之后，必须将`Build`修改为大于`6`，然后再重新打包上传

![03.png](https://i.loli.net/2020/10/16/cb3FYLaxT9uXnCH.png)

**2.**使用`xcode`打开项目的`xxx.xcworkspace`文件

![01.png](https://i.loli.net/2020/10/16/8UxCStBmVT9zn3H.png)

**3.** 在`1`的地方选择`Any iOS Device`, 接着依次选择`Product -> Archive`

![02.png](https://i.loli.net/2020/10/16/HDFMPrgUC6lwK4J.png)

**4.** 然后就是等待打包完成，完成之后，会弹出以下窗口，选择`Distribute App`

![04.png](https://i.loli.net/2020/10/16/ipAow5u9dcSYTXr.png)

**5.** 这里要注意，如果是要发布到蒲公英提交给测试扫码下载使用的话，一定要选择`Ad Hoc`, 如果是要发布到线上，一定要选择`App Store Connect`, 这里我们先选择`Ad Hoc`打测试包，点击`Next`

![05.png](https://i.loli.net/2020/10/16/nKGM6Zgh1DmWFTs.png)

**6.** 出现以下弹框，继续点击`Next`

![06.png](https://i.loli.net/2020/10/16/8eLCf4FlJDXxbPQ.png)

**7.** 然后出现以下弹框，在第二栏一定要选择`Adhoc`的描述文件（这个描述文件是开发者网站上下载的，里面包含了所有允许可以下载安装这个`app`的测试机），然后继续点击`Next`等待分析完成

![07.png](https://i.loli.net/2020/10/16/QRv21xk7Hs9l4AU.png)

**8.** 选择`Export`到你要放的位置

![08.png](https://i.loli.net/2020/10/16/cCyp5LWH4M1RaPA.png)

**9.** 这里我选择放在`下载`文件夹

![09.png](https://i.loli.net/2020/10/16/92qbEtG1FdDrufZ.png)

**10.** 最后，把下面这个包上传到蒲公英，就可以扫码下载测试啦！

![10.png](https://i.loli.net/2020/10/16/J7UKb2IHmrsilYh.png)

**11.** 接着我们讲打包上传到`App Store Connect`， 在步骤 **"5"**中，选择`App Store Connect`, 出现以下弹窗，选择`Upload`，点击`Next`，等待分析完成

![11.png](https://i.loli.net/2020/10/16/qmUGiCpZnjWSBMT.png)

出现下图，点击`Next`

![12.png](https://i.loli.net/2020/10/16/qmEkX3zTMatFbKg.png)

在第二栏一定要选择`Appstore`的描述文件（这个名字可以自己在开发者网站上自己命名），点击`Next`

![13.png](https://i.loli.net/2020/10/16/kJS2e3D16snifv9.png)

继续点击`Upload`

![14.png](https://i.loli.net/2020/10/16/E1FZrtMuLCV3l8U.png)

接着就是等待下图中的上传完成就好了

![16.png](https://i.loli.net/2020/10/16/XJHz62PM1k8YSfq.png)

最后，上传完成后，到`App Store Connect`登录苹果开发者账号，然后选择这个上传的处理完成的`ipa`包，填写相应的版本更新和其他信息，就可以提交给`Apple`审核了！

## Android打包
新建签名

keytool -genkey -alias my-key-alias -keyalg RSA -sigalg SHA1WithRSA -validity 500000 -keysize 1024 -keystore my-release-key.keystore -v

首先要修改`app/build.gradle`里面的

```
versionCode 69
versionName "3.2.0"
```

### 上传到华为应用市场

到`android`目录下，执行以下命令进行打包

```
./gradlew clean && ./gradlew assembleRelease
```

打包成功后将后缀名为`.apk`的包上传到华为应用市场提交审核即可，较为简单，不截图一一赘述了。（不懂也可以问**@雷吓光**）

### 上传到Google Play应用市场（必须翻墙）

到`android`目录下，执行以下命令进行打包

```
./gradlew clean && ./gradlew bundleRelease
```

打包成功后将后缀名为`.aab`的包上传到`Google Play`应用市场提交审核即可。大致截图如下

图一

![17.png](https://i.loli.net/2020/10/16/LvnIB5z2KQWe6d3.png)

图二

![18.png](https://i.loli.net/2020/10/16/yaeJxpj3VrWXYzg.pnga