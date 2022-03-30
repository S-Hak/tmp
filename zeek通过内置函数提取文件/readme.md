## 环境（docker基础环境测试）：

  docker pull zeekurity/zeek

  docker run -it zeekurity/zeek

## 内置文件提取脚本位置：

/usr/local/zeek/share/zeek/policy/frameworks/files/extract-all-files.zeek

## 使用测试pcap：

https://github.com/S-Hak/tmp/raw/main/zeek%E9%80%9A%E8%BF%87%E5%86%85%E7%BD%AE%E5%87%BD%E6%95%B0%E6%8F%90%E5%8F%96%E6%96%87%E4%BB%B6/main.pcap

## 测试过程：

### 使用 zeek -r 指定脚本进行流量分析

  zeek -r main.pcap /usr/local/zeek/share/zeek/policy/frameworks/files/extract-all-files.zeek
  
  运行完成后在当前目录生成运行结果：
  
![image](https://github.com/S-Hak/tmp/blob/main/images/202203301.png)


### 其中文件分析结果存储在files.log，文件存储在extract_files

  extracted对应的字段就是存储于本地的文件名

![image](https://github.com/S-Hak/tmp/blob/main/images/202203302.png)
  
  前往extract_files即可获取文件：
  
![image](https://github.com/S-Hak/tmp/blob/main/images/202203303.png)
