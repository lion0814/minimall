# 微信小程序电商平台

#### 后台管理预览：

<img src="https://s2.ax1x.com/2020/02/28/3B43RJ.png" style="zoom: 80%;" />


#### 已完成：

1. 首页页面
   - 轮播图
   - 分类列表，点击对应的分类模块，跳转至对应分类的商品
   - 商品列表，点击商品列表的某一项跳转至对应商品详情页
2. 分类页面
   -  对应的分类的商品
   - 点击商品列表项跳转到对应的商品详情页
   - 商品详情页面可以添加到购物车或收藏商品
3. 购物车页面
   -  无商品时显示默认提示信息
   - 有商品时可以通过点击按钮修改是商品数量
   - 自动计算商品价格
   - 点击结算跳转支付页面
   - 支付页面，当有默认地址时自动选择默认地址
   - 点击支付创建订单
4. 个人中心页面
   - 通过点击收藏商品按钮查看收藏商品
   - 地址管理，跳转到地址列表页面
   - 地址列表页面，可以点击创建地址信息
   - 订单列表页，可以根据不同的订单状态查看对应的订单信息




#### 修改：

1. 商品分类


2. 购物车默认提示

   ![](https://s2.ax1x.com/2020/02/24/3GJuss.png)

3. 登录授权页面

   ![](https://s2.ax1x.com/2020/02/24/3GJYz4.png)

4. 主题背景

   ![](https://s2.ax1x.com/2020/02/24/3GJBo6.png)



#### 更新一：

在商品详情页中，因为rich-text标签的体验不好，所以我选择了一个小程序的组件，wxParse,

简单易上手且强大，简单使用请查看这篇文章[微信小程序使用wxParse解析html](https://blog.csdn.net/Kotoba209_/article/details/104413748)。

以上就是完成接口数据的替换了，如想要在开发工具中校验合法域名，

<img src="https://s2.ax1x.com/2020/02/21/3m2bIP.png" style="zoom: 50%;" />

或者想要发布小程序的话，需要在微信开发者设置合法域名https://api.it120.cc，具体如下。

<img src="https://s2.ax1x.com/2020/02/21/3m2W8O.png" style="zoom: 50%;" />



#### 更新二：

1. 使用[apifm-wxapi](https://github.com/gooking/apifm-wxapi) 模块来请求数据，写法比原先的request方法更简洁，注释掉之前的request请求代码，可以直观的看到代码量的减少。这样优化可以使项目体积减少一点，[apifm-wxapi接口文档](https://github.com/gooking/apifm-wxapi/blob/master/instructions.md) 。

   apifm-使用方法：[使用 “apifm-wxapi” 快速开发小程序](https://blog.csdn.net/abccba9978/article/details/102861340) 。按照链接里的使用方法就可以请求到数据了，但是想要使用自己后台管理的数据需要在 app.js里定义一个 变量 来接收自己的域名

   `globalData: {
   ​    subDomain: "0518"
     }` 

   然后在app.js的onLaunch方法中初始化
   
    `onLaunch: *function* (*options*) {
   ​    WXAPI.init(this.globalData.subDomain);
     },`， 具体信息在项目文件中都可以找着。



#### 更新三：

1. 使用WeUI部分组件，使用教程 [WeUI使用步骤](https://blog.csdn.net/Missbelover/article/details/91950521) ；

2. 创建订单以及订单查询

   <img src="https://s2.ax1x.com/2020/02/24/3G1aUU.png" style="zoom: 80%;" />

3. 新增地址列表页，由于创建订单所需要的地址信息参数与原先的不一致，所以增加这一模块，在创建订单时提供所需的地址信息。

   <img src="https://s2.ax1x.com/2020/02/24/3G3us1.png" style="zoom: 80%;" />

4. 新增添加地址，通过提交表单创建地址信息，点击选择地区时，会有弹出选择地区。

   <img src="https://s2.ax1x.com/2020/02/24/3GGRaV.png" style="zoom:67%;" />