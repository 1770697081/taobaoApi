
这代码原来是在git上下载的，后来正好用来测试一下向github.com上提交代码用，正好这个代码可能以后有用，所以保存下来了。
123；9999;
这是要提交16.18提交的内容;
简单封装了淘宝开放平台的API调用客户端，具体参数可以通过查看API来对返回信息进行解析

### 安装

```
go get github.com/luobosoft/taobaogo
```

### 使用方法

```
package main

import (
	"fmt"
	"log"

	"github.com/luobosoft/taobaogo"
)

func main() {
	taobaogo.AppKey = ""
	taobaogo.AppSecret = ""
	taobaogo.Router = ""
	js, err := taobaogo.Request("GET", map[string]string{
		"method": "taobao.trades.sold.get",
		"fields": "tid,type,status,payment,orders,rx_audit_status",
	}, nil)
	if err != nil {
		log.Fatalln(err)
	}
	js, ok := js.Get("trades_sold_get_response").CheckGet("trade")
	if ok {
		fmt.Println(js.Map())
	}
}

```

