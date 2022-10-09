请输入esata接口配置 esataportcfg(十六进制数). <sup>[④]()</sup> 默认: 无  
usbportcfg       | ×    |-               | 如不了解请保持默认, 请输入usb接口配置 usbportcfg(十六进制数). <sup>[④]()</sup> 默认: 无  
~sn~             | ×    |-               | ~序列号. 默认根据型号随机生成.~ <sup>[②]()</sup>  
~mac~            | ×    |-               | ~MAC地址. 多个请以 "," 间隔. 默认根据型号随机生成.~ <sup>[②]()</sup>  
netif_num        | ×    |2               | 请输入网卡数量 netif_num. 默认: 2, 范围: 1~8  
vid              | ×    |"0x46f4"        | 请输入USB设备供应商识别码(Vender ID). 默认: 0x46f4  
pid              | ×    |"0x0001"        | 请输入USB设备产品识别码(Product ID). 默认: 0x0001  
diskidxmap       | ×    |-               | 请输入SATA控制器盘序 DiskIdxMap. <sup>[④]()</sup> DS920+, DS1621+, DS2422+, DVA1622 不需要填写. 默认: 无  
sataportmap      | ×    |-               | 请输入SATA控制器盘数 SataPortMap. <sup>[④]()</sup> DS920+, DS1621+, DS2422+, DVA1622 不需要填写. 默认: 无  
sasidxmap        | ×    |-               | 请输入SAS控制器盘数 SasIdxMap. <sup>[④]()</sup> DS920+, DS1621+, DS2422+, DVA1622 不需要填写. 默认: 无  
dtb              | ×    |-               | 请输入dtb 文件的下载链接(支持的文件类型: .dts,.dtb,.tar.gz,.zip), 仅 DS920+, DS1621+, DS2422+, DVA1622 需要填写, 其他型号请勿填写. [#47](https://github.com/wjz304/Redpill_CustomBuild/issues/47)  
ext              | ×    |-               | 请输入需要集成的扩展, 多个请以 "," 间隔. 支持名字（pocopico库）或者链接，名字参考[exts.json](./exts.json). eg: "r8125, tg3" 
exp              | ×    |"pocopico"      | 请选择编译依赖的基础库. "pocopico", "jumkey"  
jun              | ×    |"0"             | 仅7.0.1-42218 版本可以选择jun模式，jun模式 支持 7.0.1~7.1.1 的 DSM.  
\-               | ×    |-               | 高级自定义 <sup>[③]()</sup>  

```
①: 格式 json, key会更新到默认的user_config.json中, 因此请谨慎编写.
  - 比如 想修改 maxlanport, 需要填写完整的 synoinfo 属性, 当仅填写 {"synoinfo": {"maxlanport": "8"}} 时, 将更新 synoinfo 为只有 maxlanport, 原有 internalportcfg 将会丢失.
②: 由于SN/MAC发生盗用情况, 不再接受SN/MAC的定制, 请勿再填写.
③: body 中可直接插入shell脚本："由于权限太高, 防止有些人执行非法操作, 仅仓库作者可操作, 请联系该仓库管理员或者fork到自己名下操作."   
  - 在 body 中 以 ```xxx``` 包裹自定义的 shell 命令, 将在 build 前运行. 参考[#3](https://github.com/wjz304/Redpill_CustomBuild/issues/3) 
④：详细信息请查看：https://github.com/wjz304/Redpill_CustomBuild/issues/1252#issuecomment-1242677916
```

## 说明
0. __感谢 [hoping](https://github.com/htmambo) 大佬制作的 WEB 界面.__  
1. 构建成功 Issues 会自动 closed.  
2. 构建失败 后请调整参数重新创建Issues发起重新构建, 或者修改body后 Close Issue + Reopen 重新触发.（触发编译：open, reopen）. 
3. 再次构建, 直接 reopen 会再次触发构建. 
4. 每日构建, 打上'schedule' [【👉标签说明】](https://github.com/wjz304/Redpill_CustomBuild/blob/main/guide/Issues.md#issues-%E6%AF%8F%E6%97%A5%E5%BE%AA%E7%8E%AF%E6%9E%84%E5%BB%BA%E6%95%99%E7%A8%8B)标签 将会每日构建(通过Reopen的方式, 因此如果构建失败Issues没有Closed 将终止).  
5. 驱动的选择请参考[【👉驱动列表】](./drivers.md).     
6. 根据github官方说明所有的编译结果保留90天，周知.
7. 如果没有魔法, 参考 https://github.com/wjz304/hosts 设置 hosts.
8. [【👉问题反馈】](https://github.com/wjz304/Redpill_CustomBuild/issues/807)  交流群 QQ群: [21609194](https://qm.qq.com/cgi-bin/qm/qr?k=8AU8VJ82OR2HB_77g3vsjGKA-rm-p67B&jump_from=webapi)  TG: [https://t.me/Redpill_CustomBuild](https://t.me/Redpill_CustomBuild)  
 `(PS: 在Issues上评论我可能看不到, 邮件太多了, 如长时间未回复请私信.)`  
9. fork 本项目 Issues 和 Action 使用没有问题的.  
  但是快速创建的WEB页面由于 涉及 guthub 的 pages, 且含有CDN加速, 存在一些硬编码, 如要使用, 需要开通pages后方可使用.  
10. 在Issues下评论 "transfer" 附件转快传 🚲->🏍. (请勿重复发, 转换操作时间 ≈ 该Issue编译成功次数 X 3分钟).
11. 在Issues下评论 "delete builds" 即可删该Issues的所有历史编译记录.
12. Web页 Title 后面的红色标签是可以点击的哦!(***PS：只有读到这里的人才会知道.***)  

## 举例
* 普通参数示例:
  - {"platform":"DS3622xs+", "version":"7.0.1-42218", "ext":"r8125, tg3"}  
  - {"platform":"DS3622xs+", "version":"7.0.1-42218", "exp": "jumkey", "jun":"1", "ext":"r8125, tg3"}  
  - {"platform":"DS3622xs+", "version":"7.0.1-42218", "vid":"0x0525", "pid":"0xa4a5"}  
  - {"platform":"DS3622xs+", "version":"7.0.1-42218", "diskidxmap":"00", "sataportmap":"6", "ext":"r8125"}  
  - {"platform":"DS3622xs+", "version":"7.0.1-42218", "maxdisks":"16", "maxlanport":"7", "ext":"r8125"}  
  - {  
      "platform":"DS3622xs+",  
      "version":"7.0.1-42218",  
      "jun":"1",  
      "exp": "jumkey",  
      "netif_num":"3",  
      "ext":"r8125, r8168, e1000e, igb, vmxnet3, ixgbe"  
    }  
* dtb参数示例:
  - {"platform":"DS920+",  
      "version":"7.0.1-42218",  
      "dtb": "https://github.com/wjz304/Redpill_CustomBuildfiles/9235785/ds920p.zip",  
      "ext":"r8125"
    }  
* ext参数链接示例:
  - {  
      "platform":"DS3622xs+",  
      "version":"7.1.1-42962",  
      "ext":"r8125, e1000, e1000e, vmxnet3, https://raw.githubusercontent.com/wjz304/rp-ext/main/rtl8150/rpext-index.json"  
    }
* config参数示例:
  - {  
      "platform":"DS3622xs+",  
      "version":"7.0.1-42218",  
      "config":{"ramdisk_copy": {}},  
      "ext":"r8125, e1000, e1000e, vmxnet3"  
    }  
* 高级自定义示例:
  - {"platform":"DS3622xs+", "version":"7.0.1-42218", "jun":"1", "ext":"r8125,e1000e,vmxnet3"}  
    \`\`\`  
    echo "${platform}"  
    \`\`\`  
    
</br>
<details><summary>🍻打赏一下</summary>  
<div><img src="https://raw.githubusercontent.com/wjz304/wjz304/master/my/20220908134226.jpg" width="500"></div>  
</details>  
</br>

## 鸣谢
https://github.com/RedPill-TTG/redpill-load  
https://github.com/jumkey/redpill-load  
https://github.com/pocopico/redpill-load  
https://github.com/Online24Hours/Redpill_Build  

