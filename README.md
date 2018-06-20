在开发过程中,我们会遇到很多重复的函数使用,我将其放入一个framework中,以方便自己使用  [framework地址]()
#引入
###将``` XLToolsKit.framework```拖入项目中, 并在```embedded binaries```![引入.png](https://upload-images.jianshu.io/upload_images/4965226-24b671365bd1d63e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
中加入
#使用
### 颜色
1,系统颜色
>view.backgroundColor = XLTools.xl_white;

2,16进制颜色
>view.backgroundColor = [XLTools xlcolorWithHexColor:0xfffffc];

3, RGBA颜色
>view.backgroundColor = [XLTools xlcolorWithRed:120 green:222 blue:212 alpha:1.0];
### 窗口, 导航栏, 状态栏尺寸
>view.frame = CGRectMake(0, XLTools.xl_naviBarHeight, XLTools.xl_screenWidth, XLTools.xl_screenHeight - XLTools.xl_naviBarHeight - XLTools.xl_tabBarHeight);

###判断iPhone
>XLTools.is_xl_iPhone     是否iPhone
XLTools.is_xl_iPhone_5   是否是iPhone5的尺寸
...
XLTools.is_xl_iPhone_X

###系统时间及转换
1,格式化输出:年-月-日 时-分-秒
> NSString *currentTime = XLTools.xl_currentTime;

2, 当前时间戳
>NSString *currentTimeZone = XLTools.xl_currentTimeZone;

3, 时间戳转日期(年-月-日 时-分-秒)
>NSString *date = [XLTools timeTransFromTimestamp:currentTimeZone];

4, 时间戳转日期(按指定格式)
>NSString *date = [XLTools timeTransFromTimestamp:currentTimeZone format:@"EEE YYYY-MM-dd HH:mm:ss"];

5, 时间转时间戳
>NSString *zone = [XLTools timestampFormTime:currentTime];

###字典/数组 与JSON 相互转化
1,JSON 字符串 转 字典/数组
>NSDictionary *dic = [XLTools jsonToArrayOrNSDictionary:jsonStr];

2, 字典/数组 转 JSON
>NSString *str = [XLTools dictionaryToJson:dic];

3, 读取本地JSON文件
>NSDictionary *dic = [XLTools readLocalJSONFileWithName:@"json文件名(不带后缀.json)"];

###对数组中的对象(model)排序
```
数组:按关键字对象排序
 @param listArray 排序数组
 @param key 关键字
 @param ascending //YES 代表升序 如果为NO 代表降序
 @return 排序后对象数组
```
>NSArray <Person * >*arr = @[model1, model2];
    NSArray *sortArr = [XLTools sortArr:arr key:@"age" ascending:YES];

###获取沙盒目录路径及清理缓存
1,获取路径
> NSString *temp = XLTools.xl_tempPath;
    NSString *document = XLTools.xl_documentPath;
    NSString *cache = XLTools.xl_cachePath;

2, 获取路径下文件大小
>NSString *size = [XLTools getCacheSizeWithFilePath:cache];

3, 清除路径下文件
> BOOL isSucceed = [XLTools clearCacheWithFilePath:cache];

###判断字符串为空
>NSString *nullStr = NULL;
    BOOL result = [XLTools isEmptyString:nullStr];

###判断手机号码格式
> NSString *phoneStr = @"3254156465";
    BOOL isPhone = [XLTools isMobileNumber:phoneStr];

###判断密码格式()
```
默认(6-12位中,英文,数字;format:可nil)
NSString *password = @"gjal3 **T*hfds";
BOOL isPassword = [XLTools isPassword:password format:@"正则表达式"];
```
###根据颜色生成图片
```
UIImage *image = [XLTools imageWithColor:XLTools.xl_magenta];
```
###去掉 HTML 字符串中的标签
```
 NSString *htmlStr;
 NSString *str = [XLTools filterHTML:htmlStr];
```
###MD5加密
```
NSString *md5 = [XLTools MD5ForLower16Bate:str];
```
###BASE64 编码/解码
```
NSString *encode = [XLTools base64EncodeString:str];
NSString *decode = [XLTools base64decodeString:encode];
```
