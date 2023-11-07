## 功能总体实现图
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698390795279-3054049c-a079-41e8-a9bb-466a45b65e21.png#averageHue=%23f6f6f5&clientId=u3470c4f2-dbf4-4&from=paste&height=531&id=u6d749c11&originHeight=531&originWidth=841&originalType=binary&ratio=1&rotation=0&showTitle=false&size=33188&status=done&style=none&taskId=u13da2063-7a6c-45f3-af3d-49cf896d7c4&title=&width=841)

## 大概功能
### 微信
#### ak特性
开头为ww 
#### 使用方法
运行exe 逐步操作
```
请选择一个应用:
1. WeChat
2. DingDing
3. FeiShu
4. 退出
1
请输入 corpid: xxx
请输入 corpsecret: xx
请选择下一步操作:
1. 判断ak对应应用并获取agentid
2. 获取通讯录
3. 后利用模式
4. 邀请加入企业
5. 退出
```
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698126793255-4403ebb7-7448-4540-b7c5-11fcd4ecf42c.png#averageHue=%23131313&clientId=u4548feb0-88d9-4&from=paste&height=331&id=ubaf9fb91&originHeight=331&originWidth=556&originalType=binary&ratio=1&rotation=0&showTitle=false&size=15738&status=done&style=none&taskId=u30ab6e4e-2319-4750-80e2-d09fcaa4a99&title=&width=556)

目的:泄露企业微信key，获取后的后利用，包含获取组织架构，整体通讯录，后续钓鱼社工利用。
功能:分为四大模块，分别为判断ak对应应用、获取通讯录、后利用模式、邀请加入企业。
1、可以通过判断ak对应应用去定位我们获取了哪个应用的api权限。
2、一般应用都有调用获取通讯录api的权限，获取通讯录可方便我们后续利用。
3、后利用模式分为上传文件、下载文件和下发消息功能，第一步上传我们的木马或者钓鱼话术文件至企业微信存储桶中，然后通过通讯录定位社工钓鱼的人，进行定点发送我们的木马或者是钓鱼话术，从而达到钓鱼的作用。
4、邀请加入企业模块，需要比较高权限的ak，拥有高权限ak后可自动生成二维码，扫描填写信息即可加入企业。

#### 1、判断ak对应的应用
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698398404635-d598edc4-15f3-4e4d-bc13-45ebdf97fdf5.png#averageHue=%231c1919&clientId=u2be072fa-fe3d-4&from=paste&height=541&id=u61c710e5&originHeight=541&originWidth=1134&originalType=binary&ratio=1&rotation=0&showTitle=false&size=247119&status=done&style=none&taskId=ua14eda47-052f-4af0-bd0f-ebf39a48f7a&title=&width=1134)
#### 2、获取全员通讯录
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698398358211-4685b27c-6137-4026-8aa0-0503bb7d531f.png#averageHue=%23202020&clientId=u2be072fa-fe3d-4&from=paste&height=503&id=u2514f88e&originHeight=503&originWidth=1028&originalType=binary&ratio=1&rotation=0&showTitle=false&size=255930&status=done&style=none&taskId=uf038d271-6dcc-48cf-98e3-6cae614303d&title=&width=1028)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698398382049-268ef14a-4940-47a3-a3a1-7990b163c3b3.png#averageHue=%23f5f5f5&clientId=u2be072fa-fe3d-4&from=paste&height=606&id=u404a234b&originHeight=606&originWidth=831&originalType=binary&ratio=1&rotation=0&showTitle=false&size=106224&status=done&style=none&taskId=u6712a4a9-d403-4fbd-9731-66f6b90a893&title=&width=831)
#### 3、后利用模式

##### 上传文件
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698398327474-f30b265e-c620-4864-b952-c919efd61e14.png#averageHue=%23181818&clientId=u2be072fa-fe3d-4&from=paste&height=235&id=ud8373128&originHeight=235&originWidth=938&originalType=binary&ratio=1&rotation=0&showTitle=false&size=69276&status=done&style=none&taskId=ud229f54e-69aa-469a-a47e-4488d5bf4f3&title=&width=938)
##### 下载文件
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698398287099-b389fc17-e1a7-4006-b608-f2f20a7c639f.png#averageHue=%23696565&clientId=u2be072fa-fe3d-4&from=paste&height=201&id=u38e14238&originHeight=201&originWidth=945&originalType=binary&ratio=1&rotation=0&showTitle=false&size=66719&status=done&style=none&taskId=u4c41dc36-1549-41e2-8964-77883d7ac1a&title=&width=945)
##### 发送消息![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698398193999-76c5df69-17dd-4ea6-a363-f54eb7d5438d.png#averageHue=%23161616&clientId=u2be072fa-fe3d-4&from=paste&height=206&id=u72971eca&originHeight=206&originWidth=902&originalType=binary&ratio=1&rotation=0&showTitle=false&size=73211&status=done&style=none&taskId=ub045b07a-2829-44ab-9293-3689939822f&title=&width=902)
传入用户id(由通讯录获取) mediaid(上传文件后回显的id) agentid(刚开始获取的应用Id)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698398128106-d455c52a-80d0-418f-8a8f-c39bf8c89170.png#averageHue=%23cad3e6&clientId=u2be072fa-fe3d-4&from=paste&height=625&id=uf38ae2f9&originHeight=728&originWidth=666&originalType=binary&ratio=1&rotation=0&showTitle=false&size=64347&status=done&style=none&taskId=uecd62018-71fe-48ef-8f2e-836eb0913e4&title=&width=572)
#### 4、邀请加入企业
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698398077781-20d815af-2e7c-436d-850c-6f7ab1087224.png#averageHue=%23171717&clientId=u2be072fa-fe3d-4&from=paste&height=220&id=u4daa06ef&originHeight=220&originWidth=947&originalType=binary&ratio=1&rotation=0&showTitle=false&size=81812&status=done&style=none&taskId=u93e0e55d-5182-4d55-93cb-d280275e840&title=&width=947)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698398099370-d6ae4c68-0357-43a4-acd5-96f0c4f00377.png#averageHue=%23484848&clientId=u2be072fa-fe3d-4&from=paste&height=492&id=u83143bf7&originHeight=492&originWidth=875&originalType=binary&ratio=1&rotation=0&showTitle=false&size=134120&status=done&style=none&taskId=uf5b345ac-00fb-48aa-859e-9569d13d57f&title=&width=875)

### 钉钉
#### ak特性
开头为ding

#### 使用方法
运行exe 逐步操作
```
请选择一个应用:
1. WeChat
2. DingDing
3. FeiShu
4. 退出
2
请输入appKey: xxxx
请输入appSecret: xxx
Access Token: xxxx
请选择一个操作:
1. 获取通讯录
2. 邀请进入组织
3. 创建企业账号
4. 删除企业账号
```

![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698127396589-fe4a69f4-a538-4147-870e-487a1bbd96c7.png#averageHue=%23141414&clientId=u4548feb0-88d9-4&from=paste&height=229&id=u3dcfeb1a&originHeight=229&originWidth=678&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13592&status=done&style=none&taskId=u2a0e2133-3509-44c2-b1e5-9276f2cdc28&title=&width=678)

目的:泄露钉钉应用key的后利用，包括获取token，获取通讯录，获取企业邀请链接，添加删除企业高管用户。
功能:分为三大模块，分别为获取通讯录、获取企业邀请链接、添加删除企业高管用户。
1、通过泄露的ak获取token，在具有通讯录的权限以及白名单的情况下获取通讯录
2、通过接口调用获取企业邀请链接，可填写内容进入企业。
3、调用接口自定义请求包，创建高管用户，高管用户(隐藏手机号、DING等消息)
4、可以删除创建的企业账号
#### 1、一键获取企业通讯录
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698397549213-0e082533-9b49-4e45-95f0-532d030c43de.png#averageHue=%23161616&clientId=u2be072fa-fe3d-4&from=paste&height=196&id=u6e6f6b4d&originHeight=196&originWidth=711&originalType=binary&ratio=1&rotation=0&showTitle=false&size=6952&status=done&style=none&taskId=ufd814fee-241e-4c85-80f5-b6775c45adb&title=&width=711)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698397655598-c859f172-de00-4ac5-8ddb-6e751bf21888.png#averageHue=%23efeeed&clientId=u2be072fa-fe3d-4&from=paste&height=529&id=u9456221f&originHeight=529&originWidth=1920&originalType=binary&ratio=1&rotation=0&showTitle=false&size=81546&status=done&style=none&taskId=u72ead464-7c4b-47ef-afaf-9d1d03bf088&title=&width=1920)
#### 2、获取企业邀请链接(需要审批)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698397729763-e6db01ea-7359-4781-a079-70857318cccf.png#averageHue=%23161616&clientId=u2be072fa-fe3d-4&from=paste&height=205&id=u5bea98c2&originHeight=205&originWidth=968&originalType=binary&ratio=1&rotation=0&showTitle=false&size=9335&status=done&style=none&taskId=u5e238bd4-3274-4adb-964e-56be14f3ec1&title=&width=968)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698397752478-f283cd8b-17d0-49e7-9493-e87d8a90d9ba.png#averageHue=%23f8f8f8&clientId=u2be072fa-fe3d-4&from=paste&height=704&id=u67287fb3&originHeight=704&originWidth=1176&originalType=binary&ratio=1&rotation=0&showTitle=false&size=38822&status=done&style=none&taskId=uc69be14a-77ad-4b3c-beee-9a9f8a0b202&title=&width=1176)
#### 3、添加企业用户(高管模式)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698397825501-00a110e6-29c4-4ade-9f9c-164a434f413a.png#averageHue=%23222222&clientId=u2be072fa-fe3d-4&from=paste&height=235&id=ud83d5e52&originHeight=235&originWidth=420&originalType=binary&ratio=1&rotation=0&showTitle=false&size=76891&status=done&style=none&taskId=ud0c083ec-b391-4f37-adbb-f0bc5840e0b&title=&width=420)v
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698397830108-ce36e834-97cc-4feb-8f94-fa8bcfdfa887.png#averageHue=%23edf0ec&clientId=u2be072fa-fe3d-4&from=paste&height=866&id=ucfcbfa95&originHeight=866&originWidth=863&originalType=binary&ratio=1&rotation=0&showTitle=false&size=181146&status=done&style=none&taskId=u28fdb4df-9ff1-408c-8840-a5493b89f72&title=&width=863)
#### 4、删除已创建的企业账号
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698397896207-a7dee46e-7a02-4719-8ba8-a10d54310db0.png#averageHue=%23161616&clientId=u2be072fa-fe3d-4&from=paste&height=146&id=u0ddb49ae&originHeight=146&originWidth=604&originalType=binary&ratio=1&rotation=0&showTitle=false&size=5263&status=done&style=none&taskId=uabcc06bc-711a-4eb4-9a31-a9efb709558&title=&width=604)



### 飞书
#### ak特性
开头为cli_
#### 使用方法
```
请选择一个应用:
1. WeChat
2. DingDing
3. FeiShu
4. 退出
3
请输入 App ID: xxxx
请输入 App Secret: xxxx
请选择下一步操作:
1. 获取企业全员通讯录
2. 创建用户
3. 删除用户
4. 消息操作
5. 退出
```

![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698131150654-a7a958ff-124b-4c94-be72-e1d7c2959859.png#averageHue=%23191919&clientId=u4548feb0-88d9-4&from=paste&height=283&id=u8cb22248&originHeight=283&originWidth=465&originalType=binary&ratio=1&rotation=0&showTitle=false&size=14570&status=done&style=none&taskId=u6882c118-415a-4c7c-b429-f3ae25f360a&title=&width=465)
目的:泄露飞书应用key的后利用，包括获取token,获取通讯录,创建删除用户，消息推送功能
1、首先通过获取的token遍历所有组织号，然后通过组织号获取所有人员通讯录
2、通过接口创建别人看不到手机号的用户
3、删除创建的用户，通过userid
4、消息操作分为上传文件、下载文件和下发消息功能，第一步上传我们的木马或者钓鱼话术文件至存储桶中，然后通过通讯录定位社工钓鱼的人，进行定点发送我们的木马或者是钓鱼话术，从而达到钓鱼的作用。
#### 1、通讯录导出
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698215273712-93f97f22-e734-4464-a198-63d1a2df62da.png#averageHue=%23191919&clientId=ue8d7f862-c068-4&from=paste&height=199&id=u902a2749&originHeight=199&originWidth=493&originalType=binary&ratio=1&rotation=0&showTitle=false&size=6603&status=done&style=none&taskId=u7ac99f01-9f6c-42fd-86ac-56a5f25c8bd&title=&width=493)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698215304401-cc622902-43a8-4ed8-8973-c81013429469.png#averageHue=%23f6f6f5&clientId=ue8d7f862-c068-4&from=paste&height=332&id=u19179531&originHeight=332&originWidth=1479&originalType=binary&ratio=1&rotation=0&showTitle=false&size=20519&status=done&style=none&taskId=u611a4dc4-5f6d-422d-a5f9-3c6adf261f5&title=&width=1479)
#### 2、创建删除用户
##### 创建用户
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698215385314-0947dd9c-3708-44ee-af7b-737e0c1002f6.png#averageHue=%23171717&clientId=ue8d7f862-c068-4&from=paste&height=165&id=u80f2de79&originHeight=165&originWidth=498&originalType=binary&ratio=1&rotation=0&showTitle=false&size=4699&status=done&style=none&taskId=u4db21c28-1334-4e18-b873-efcb55d1b83&title=&width=498)
![660f4410f15668dbb65061c469c0933.jpg](https://cdn.nlark.com/yuque/0/2023/jpeg/22598157/1698215475369-90b76a10-e5ba-44a3-bee6-87c7c53424cc.jpeg#averageHue=%23cecfcb&clientId=ue8d7f862-c068-4&from=paste&height=439&id=ua5e553dd&originHeight=952&originWidth=1170&originalType=binary&ratio=1&rotation=0&showTitle=false&size=200143&status=done&style=none&taskId=u2e5f9943-bea5-4f01-8493-fd0ecc2827b&title=&width=540)
点击链接则可加入企业
![678c530713e11c88abb468275dbc4fc.jpg](https://cdn.nlark.com/yuque/0/2023/jpeg/22598157/1698215526478-9dee9f16-2b33-47e8-9f4f-d2d44be89eff.jpeg#averageHue=%23fcfbf6&clientId=ue8d7f862-c068-4&from=paste&height=659&id=ua7ef2d87&originHeight=1684&originWidth=1170&originalType=binary&ratio=1&rotation=0&showTitle=false&size=232538&status=done&style=none&taskId=u86c45bd9-5902-462c-86ec-a7fa416098e&title=&width=458)
##### 删除用户
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698215620902-bd3311fe-bd49-4c83-9550-a3ad19db18af.png#averageHue=%231b1b1b&clientId=ue8d7f862-c068-4&from=paste&height=151&id=u81f8dd62&originHeight=151&originWidth=364&originalType=binary&ratio=1&rotation=0&showTitle=false&size=4300&status=done&style=none&taskId=ud5278a2f-22b8-4ea1-92d2-62714a76129&title=&width=364)
通过提供八位user_id删除用户
#### 3、消息操作
分为上传文件、下载文件、发送消息
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698215779173-14ebc04d-3728-4b72-9c48-7183f1f7e35f.png#averageHue=%23222222&clientId=ue8d7f862-c068-4&from=paste&height=87&id=ub1e19c79&originHeight=87&originWidth=171&originalType=binary&ratio=1&rotation=0&showTitle=false&size=2123&status=done&style=none&taskId=u04289c0d-3c82-4699-89c7-50206862a8c&title=&width=171)
##### 上传文件
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698215763397-6280d9d5-3af0-4f6d-aa17-b419099abbbd.png#averageHue=%23171717&clientId=ue8d7f862-c068-4&from=paste&height=148&id=ud0f3ac08&originHeight=148&originWidth=587&originalType=binary&ratio=1&rotation=0&showTitle=false&size=5891&status=done&style=none&taskId=ud84a6383-30cf-45ed-aa1d-ec65e39d958&title=&width=587)
给出file key
##### 发送消息
通过file key和user id去发送给指定人员
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698215891623-d4419008-7944-444c-b71c-44311cb73432.png#averageHue=%231c1c1c&clientId=ue8d7f862-c068-4&from=paste&height=67&id=u4b66feea&originHeight=67&originWidth=606&originalType=binary&ratio=1&rotation=0&showTitle=false&size=3446&status=done&style=none&taskId=u0966e54d-e61c-4e02-b254-3c31115d1d6&title=&width=606)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/22598157/1698215932535-81cf8896-d840-47d5-9834-2de8e8f17932.png#averageHue=%23fefbef&clientId=ue8d7f862-c068-4&from=paste&height=229&id=ub3568732&originHeight=229&originWidth=442&originalType=binary&ratio=1&rotation=0&showTitle=false&size=8219&status=done&style=none&taskId=ua4f39330-5052-4f3b-b163-bfd21756fb6&title=&width=442)

