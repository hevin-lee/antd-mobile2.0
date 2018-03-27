# antd-mobile2.0
最近研究antd-mobile2.0 ，官网一直也没给出详细的配置过程，根据自己的不断尝试，总有有些结果了~~


配置过程如下：

## 配置config.dev.js


const theme = require('../package.json').theme;

{
            test:/\.(css|less)$/,
            use: [
              {
                loader: require.resolve('postcss-loader'),
                options: {
                  ident: 'postcss',
                  plugins: () => [
                    px2rem({remUnit: 75 , propWhiteList: []}) ,    //重点    //设计稿根据750px(iphone6)
                  ],
                },
              },
              {
                loader: require.resolve('less-loader'),
                options: {
                  modifyVars: theme //重点
                },
              },
             ]
}
              
## 配置package.json

增加配置
{
  "theme": {
    "hd":"2px", //重点高清配置2倍
    "@primary-color": "#ce4f35"
  }
}


## html模板配置

html代码在head里面引入 <script src="http://g.tbcdn.cn/mtb/lib-flexible/0.3.4/??flexible_css.js,flexible.js"></script> 即可，也可以直接保存到本地，引入也可
              


以上配置均基于750设计稿


配置过程大概如上，如有什么不对的地方，还欢迎指正、交流。
