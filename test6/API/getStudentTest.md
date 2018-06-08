# 接口：getStudentTest  [返回](../README.md)
用例： [实验列表](../UseCase/实验列表.md)

- 功能：
    登录到平台。

- 权限：
    学生。

- API请求地址：
    接口基本地址/v1/api/getStudentTest

- 请求方式 ：
    POST

- 请求实例：

```
 {
      "status": true,
      "info": "获取结果成功",
      "total": 36,
      "data": [
          {
          "ID":19,
          "Test_NO":"10023",
          "TITLE":"****",
          "CONTENT": "内容",
          "STATUS":"1",
          ...
          },

          {
          ...其他课程
          }
      ]
  }

```

- 请求参数说明:

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|
  |id|学生学号或者老师的工号，由type决定。|
  |password|用户的密码，不是原文，是加密后的字符串|
  |type|用户类型，学生或者老师|

- 返回实例：

        {
            "status": true,
            "info": null,
        }

- 返回参数说明：

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|

