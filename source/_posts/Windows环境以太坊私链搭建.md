---
title: Windows环境以太坊私链搭建
comments: true
date: 2018-05-04 11:10:22
tags: 
   - 虚拟货币
   - 以太坊
   - 区块链
categories: 区块链
---

做以下准备：

1. win10系统，64位 

2. 以太坊钱包 

3. 以太坊geth客户端 

​     geth 和 钱包可以到ethfans.org的资料库里下载，那里提供国内镜像和官网地址。  

​     钱包工具：<https://ethfans.org/wikis/Ethereum-Wallet-Mirror>  

​     geth :<https://ethfans.org/wikis/Ethereum-Geth-Mirror>  



创建创世块文件 genesis.json

```json
{
  "config": {
        "chainId": 15,
        "homesteadBlock": 0,
        "eip155Block": 0,
        "eip158Block": 0
    },
  "alloc"      : {},
  "coinbase"   : "0x0000000000000000000000000000000000000000",
  "difficulty" : "0x2000",
  "extraData"  : "",
  "gasLimit"   : "0x2fefd8",
  "nonce"      : "0x0000000000000042",
  "mixhash"    : "0x0000000000000000000000000000000000000000000000000000000000000000",
  "parentHash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
  "timestamp"  : "0x00"
}
```

| 字段名     | 含义                                                         |
| ---------- | ------------------------------------------------------------ |
| nonce      | nonce就是一个64位随机数，用于挖矿，注意他和mixhash的设置需要满足以太坊的Yellow paper, 4.3.4. Block Header Validity, (44)章节所描述的条件。 |
| difficulty | 设置当前区块的难度，如果难度过大，cpu挖矿就很难，这里设置较小难度 |
| alloc      | 用来预置账号以及账号的以太币数量，因为私有链挖矿比较容易，所以我们不需要预置有币的账号，需要的时候自己创建即可以。 |
| coinbase   | 矿工的账号，随便填                                           |
| timestamp  | 设置创世块的时间戳                                           |
| parentHash | 上一个区块的hash值，因为是创世块，所以这个值是0              |
| extraData  | 附加信息，随便填，可以填你的个性信息                         |
| gasLimit   | 该值设置对GAS的消耗总量限制，用来限制区块能包含的交易信息总和，因为我们是私有链，所以填最大。 |
| mixhash    | 与nonce配合用于挖矿，由上一个区块的一部分生成的hash。注意他和nonce的设置需要满足以太坊的Yellow paper, 4.3.4. Block Header Validity, (44)章节所描述的条件。. |

初始化区块链

```shell
geth --identity "PICCetherum" --rpc --rpccorsdomain "*" --datadir "./data" --port "30303" --rpcapi "db,eth,net,web3" --networkid 95518 console
```

创建用户

```C#
personal.newAccount()
```

启动钱包可视化软件

```shell
 jar -xvf  迭代9需求.zip
```

