### HTTP发送请求过程
- 对目标域名进行DNS解析，获取到IP地址
- 根据获取到的IP找到对应的服务器，发起TCP的三次握手
- 建立TCP连接后发送HTTP请求
- 服务器相应HTTP请求，浏览器得到HTML代码
- 浏览器解析HTML代码，并将HTML代码中的资源(脚本文件js,css)
- 浏览器渲染页面

### 浏览器发送请求的几种方式
- GET请求，主要是将参数包含在URL中
    - GET请求返回时不会产生副作用
    - GET请求只能进行URL编码
    - GET请求对于参数长度有限制
    - GET请求直接暴露参数
    - GET会被浏览器主动Cache
- POST请求，主要是讲参数包含在HTTP请求的Body中
    - POST参数长度不受限制
    - POST请求可以设置请求参数和返回参数的格式，如XML，JSON格式

# 请求百度获取数据 
```python
import requests
response = requests.get('https://www.baidu.com')

# decode in utf-8
response.encoding = 'utf-8'
if response.status_code == 200:
    print(response.text)
```
    

### 常用的HTTP返回参数
- response code
    - 2xx 返回成功
        - 200 请求完成
    - 3xx
        - 301 已经移动到新位置
        - 302 已找到
        - 305 使用代理
        
    - 4xx
        - 400 请求错误，语法有问题
        - 401 需要授权
        - 404 资源未找到
        
    - 5xx
        - 500 内部服务错误
- request method
    - get
    - post
    - put
    - delete
- response headers
    - content-type 返回数据类型
- request headers
    - method 方法
    - path 路径
    - accept 接受数据形式
    - user-agent 浏览器代理
    
### 如何添加请求头
```python
import json
import requests
url = 'https://xxx.xxx./api/version'

payload = {"key": "value"}
headers = {'content-type': 'application/json'}
r = requests.post(url, data=json.dumps(payload), headers=headers)

```