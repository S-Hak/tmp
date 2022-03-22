

## Malcolm 认证方式使用的基础http认证，可通过脚本添加相应头来调用Malcolm内部接口
  ````
  headers = {"Authorization": "Basic YWRtaW46MTIzNDU2"}
  ````



## 首先通过搜索语句获取搜索结果，代码示例：
  ````
  def cat_id():
    urls = "https://10.2.51.242/api/sessions"
    bodys = {
      "flatten": 1,
      "length": 50,
      "facets": 1,
      "bounding": "last",
      "interval": "auto",
      "expression": "oracle.host == desktop-rpl214p",             #搜索语句
      "startTime": 1643677434,                                     #开始时间
      "stopTime": 1648087434,                                     #结束时间
      "order": "firstPacket:desc",
      "fields": "ipProtocol,protocol,event.dataset,firstPacket,lastPacket,source.ip,source.geo.country_iso_code,source.port,destination.ip,destination.geo.country_iso_code,destination.port,network.packets,totDataBytes,network.bytes,tags,http.uri,email.src,email.dst,email.subject,email.filename,dns.host,cert.alt,irc.channel"       #需要返回的数据
      }
    responce = requests.post(url=urls,headers=headers,data=bodys,verify=False)
    result = responce.json()
    return result
````

### 请求后数据会返回到result中的result['data']，其中第一项的ID值为result['data'][0]['id']

## 通过ID获取 Malcolm解析后的数据包:
### url中的其他参数与Malcolm界面选项一一对应，根据需求进行更改，示例代码如下：
```
  def cat_data():
    id = "3@220315-CgEV3UecZ3xMqZrOpoAKg_EO"
    urls = """
    https://10.2.51.242/arkime/session/%s/packets?base=ascii&line=false&image=false&gzip=false&ts=false&decode={}&packets=200&showFrames=false&showSrc=true&showDst=true
    """ % id
    responce  = requests.get(urls,headers=headers,verify=False)
    return responce.text
```

### 返回的数据为带有html展示特性的数据，经过过滤后可提取到oracles payload























