# 交通联合卡

## 卡片结构

``` mermaid
graph LR
    mf[[MF<br>AID=325041592E5359532E4444463031]]
    mf --> ec[[电子现金<br>AID=A000000632010106]]
    mf --> ep[[电子钱包<br>AID=A000000632010105]]
    ec --> payment[支付应用专用文件<br>SFI=0x01-0x04]
    ec --> purchase[消费交易明细文件<br>SFI=0x0B]
    ec --> load[圈存交易明细文件<br>SFI=0x0C]
    ec --> issue[发卡机构自定义文件<br>SFI=0x15-0x19]
    ec --> pubrecord[公共交通过程信息变长记录文件<br>SFI=0x1A]
    ec --> pubcircle[公共交通过程信息循环记录文件<br>SFI=0x1E]
    ec --> 余额文件
    ep --> 余额文件
    ep --> pubrecord
    ep --> pubcircle
    ep --> issue1[公共应用基本文件<br>SFI=0x15]
    ep --> holder[持卡人基本信息文件<br>SFI=0x16]
    ep --> management[管理信息文件<br>SFI=0x17]
    ep --> transactions[交易明细文件<br>SFI=0x18]
    ep --> issue2[发卡机构自定义文件<br>SFI=0x05-0x08,0x19]
```

注意，交通联合卡采用一卡双应用的方式发行，电子现金和电子钱包应用共享余额和公共交通过程数据。