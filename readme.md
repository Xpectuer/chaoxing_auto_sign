## 功能描述

创建Autosign对象

参数为手机号码和密码，也支持学号登录，学号登录需要手动获取fid值(操作在下方)

支持普通签到，手势签到，二维码签到，位置签到，拍照签到

## 如何使用？
1. 使用接口，自动24小时签到
    参考此文
    https://www.z2blog.com/index.php/default/459.html

2. 自己有服务器
    稍加修改代码，挂在自己的服务器上定时执行


## 接口使用(非长期有效)

```
http://101.89.182.58:9090/sign/
```

请求代码示例：
```python
params = {
    'username': 'xxxxx',
    'password': 'xxxxx',
    'schoolid': '',
}
requests.post('http://101.89.182.58:9090/sign/', params=params)
```

在线接口调试：
http://101.89.182.58:9090/docs#/default/sign_sign__post


| 请求方式 |   参数   |  说明  | 是否必须 |
| :------: | :------: | :----: | :------: |
|          | username |  账号  |    是    |
|   **POST**   | password |  密码  |    是    |
|          | schoolid | 学校ID |    否    |
| | sckey | server酱key | 否 |


**如果是学号登录，fid参数必填**

### 如何获取FID
关于学号登录方式，有一个额外参数`schoolid`

http://passport2.chaoxing.com/login

![schoolid][5]


## 其他签到脚本推荐


| 项目地址                                                | 开发语言   | 备注                                           |
| ------------------------------------------------------- | ---------- | ---------------------------------------------- |
| https://github.com/Wzb3422/auto-sign-chaoxing           | TypeScript | 超星学习通自动签到，梦中刷网课       |
| https://github.com/Huangyan0804/AutoCheckin             | Python     | 学习通自动签到，支持手势，二维码，位置，拍照等 |
| https://github.com/aihuahua-522/chaoxing-testforAndroid | Java       | 学习通（超星）自动签到               |
| https://github.com/yuban10703/chaoxingsign              | Python     | 超星学习通自动签到                   |



## 更新日志
4.3
- 简化courseid和classid提取

4.2
- 修复多用户多签到任务bug

3.21
- 加入activeid缓存，会将所有签到成功的activeid记录在activeid.txt,避免重复触发签到

3.20 
- 加入server酱，签到消息可推送至微信
- 纠正因证书问题，导致运行过程中，输出大量异常消息
- 优化签到类型的逻辑判断

3.18 新增二维码，拍照，位置签到

3.18 修复登录失败问题

3.17 更新手势签到，无需手动输入验证码

3.15 支持学号方式登录,目前可以通过(手机号码，邮箱，学号登录)

3.10 新增手势签到


## 扩展
1. 配合fastapi，挂到服务器上，定时请求，全天自动签到
2. 做成QQ或微信机器人插件，可以面向大众用户使用
3. 结合Server酱，可以将签到结果推送给用户微信
