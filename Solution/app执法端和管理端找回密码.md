---
title: app执法端和管理端找回密码
tags: 执法端,管理端,找回密码
---


同app市民端
#### 获取短信验证码 ####
	url：http://192.168.1.12/zhcs/appusrmngController/getCodeByEmail.do
    post参数：
    {
      "email":"1313213@132.com ",
      "genre":"2" // 表示找回密码 
    }
	返回数据
    {
  	  "result": "01"
    }
// 这时候会下发验证码到邮箱
#### 找回密码 ####
	url:http://192.168.1.12/zhcs/appusrmngController/forgetPwdByEmail.do
    post参数：
    {
     "email": "1313213@132.com",
     "password": "e10adc3949ba59abbe56e057f20f883e", // 新密码
     "code": "1234" // 邮箱验证码
    }
	返回数据
    {
      "result": "01",
      "token": "215f7f07af294fb6129a933dedf95892"
    }


##### 最后更新时间 2016年12月6日10:11:14