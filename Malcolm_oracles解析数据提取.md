

## Malcolm 认证方式使用的基础http认证，可通过脚本添加相应头来调用Malcolm内部接口

  headers = {"Authorization": "Basic YWRtaW46MTIzNDU2"}



首先通过搜索语句获取搜索结果，代码示例：
  urls = "https://10.2.51.242/api/sessions"
  bodys = {
    "flatten": 1,
    "length": 50,
    "facets": 1,
    "bounding": "last",
    "interval": "auto",
    "cancelId": "72e31dc6-dedd-4c67-a36e-ac66ec596314",
    "expression": "oracle.host == desktop-rpl214p",             #搜索语句
    "startTime": 1643677434,        #开始时间
    "stopTime": 1648087434,         #结束时间
    "order": "firstPacket:desc",
    "fields": "ipProtocol,protocol,event.dataset,firstPacket,lastPacket,source.ip,source.geo.country_iso_code,source.port,destination.ip,destination.geo.country_iso_code,destination.port,network.packets,totDataBytes,network.bytes,tags,http.uri,email.src,email.dst,email.subject,email.filename,dns.host,cert.alt,irc.channel"
    }
  responce = requests.post(url=urls,headers=headers,data=bodys,verify=False)
  result = responce.json()

