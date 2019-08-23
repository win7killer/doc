# webpack 的 output.publicPath 变量设置
> 个人笔记使用，非对外文章

> 使用与以下情况：
- 根据不同的编译参数，确定不同的 publicPath
- 根据运行环境的具体情况确定
- 后端[php为例]确定 cdn

### 具体：

#### webpack 配置
```js
module.exports = {
    ...
    output: {
        publicPath: undefined, // 或者不配置该项
    }
    ...
    plugins: [
        new htmlWebpackPathPlugin({
            publicPath: process.env.B_ENV === 'pre' ? '//pre-static.cdn.com/' : '<?CDN_URL>'
        })
    ]
};

```


#### 前端自己区分环境
- 入口js文件
```js
__webpack_public_path__ = location.hostname === 'www.a.com' ? '//a.cnd.com' : '//b.cdn.com'

```
#### 后端决定

- html 需要 php 渲染输出 【node 同理】
```html
<script>
    var CDN_URL = '<?CDN_URL>'; // <?CDN_URL> 为 php 常量
</script>
```
- 入口js文件
```js
__webpack_public_path__ = window.CDN_URL;

```
- webpack 额外配置 // 处理 html-webpack-plugin 自动注入之后的静态资源的域名，实际上就是做了替换操作
``` js
new htmlWebpackPathPlugin({
     publicPath: '<?CDN_URL>'
})
```

### 根据编译脚本处理
- package.json
```json
"build": "webpack ./webpack.conf.js",
"build:pre": "cross-env B_ENV=pre webpack ./webpack.conf.js ",
"build:beta": "cross-env B_ENV=beta webpack ./webpack.conf.js ",

```

- webpack 额外配置 // 处理 html-webpack-plugin 自动注入之后的静态资源的域名，实际上就是做了替换操作
``` js
new htmlWebpackPathPlugin({
     publicPath: process.env.B_ENV === 'pre' ? '//pre.cdn.com' : '//cdn.com' // beta
})
```
