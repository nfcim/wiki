# 北京市政交通一卡通 

## 卡片结构

``` mermaid
graph TD
    mf[[MF<br>AID=325041592E5359532E4444463031<br>DF-ID=0x3F00]] --> issue[发行信息<br>SFI=0x04]
    mf --> basic[基本信息<br>SFI=0x05]
    mf --> purse[[钱包应用<br>EF-ID=0x1001]]
    purse --> topup[充值记录<br>SFI=0x13]
    purse --> bus[公交数据<br>SFI=0x14]
    purse --> metro[地铁数据<br>SFI=0x15]
    purse --> trans[交易明细<br>SFI=0x18]
```

## 文件结构

### MF
#### 发行基本信息文件

| 基本属性  | 值   |
|---------|------|
| SFI     | 0x04 |
| 文件类型 | 二进制 |
| 文件大小 | 0x3C |
| 权限    | 读=自由，写=SM |

| 字节   | 数据元     | 长度 | 数据类型 | 备注 
|-------|-----------|-----|---------|--
| 1-8   | 卡号       | 8   | BCD     | 
| 9-24  | 不详       | 15  | N/A     | 
| 25-28 | 发行日期    | 4   | BCD     | YYYYMMDD
| 29-32 | 失效日期    | 4   | BCD     |YYYYMMDD
| 33-60 | 不详       | 28  | N/A     | 

#### 公共基本信息文件

| 基本属性  | 值   |
|---------|------|
| SFI     | 0x05 |
| 文件类型 | 二进制 |
| 文件大小 | 0x20 |
| 权限    | 读=自由，写=SM |

| 字节   | 数据元     | 长度 | 数据类型 | 备注 
|-------|-----------|-----|---------|--
| 1 - 3 | 透支金额    | 3  | HEX     |
| 4 - 5 | 累计交易计数 | 2  | HEX     |
| 6 - 32 |不详       | 27 | N/A     |

### 钱包应用

#### 充值记录文件

#### 公交刷卡数据文件

#### 地铁刷卡数据文件

#### 交易明细记录文件

### 地铁线路数据

## 备注

1. 由于 MF 默认选中，因此读卡器不会发送 `SELECT` 命令，但如果手动发送 `SELECT` 命令，该卡也会接受。
2. 由于该卡接受的 AID 为 PPSE，因此在目前的 iOS 上无法读取。