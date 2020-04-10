# Translate API
基于 [translate-platforms](https://www.npmjs.com/package/translate-platforms) 多平台翻译库。

# 调用方式

FormData 请求:
```javascript
function translate() {
    let param = new FormData();
    let error = '';
    let result = '';

    param.append('platform', 'google')
    param.append('word', 'test')
    param.append('from', 'en')
    param.append('to', 'zh')

    axios.post(this.api, param, {
        headers: {
            'Content-Type': 'multipart/form-data'
        }
    }).then(rsp => {
        rsp = rsp.data;
        if (rsp.status) {
            error = rsp.msg;
            return;
        }
        result = rsp.data.word;
    }).catch(err => {
        error = err.message;
    })
}
```

## 接口参数
|键|说明|
|--|--|
|platform|翻译平台|
|word|要翻译的内容|
|from|来源语言，auto 或不传则自动识别|
|to|目标语言|

## 响应内容
|键|说明|
|--|--|
|status|状态码|
|msg|状态信息|
|data|翻译结果|
|- lang|来源语言与目标语言|
|- word|要翻译的内容|
|- text|翻译的结果|
|- candidate|其他候选翻译结果|

## 部署说明
- 运行服务只需运行 `npm start`