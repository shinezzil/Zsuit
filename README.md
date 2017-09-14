![Alt text](http://oph42y401.bkt.clouddn.com/Upload-Image-20170914120734_420.png)

#商品SKU组合查询插件
本插件使用JavaScript实现，测试页面依赖jQuery-1.8.1.js

#常用方法
    实例化对象
```javascript
    var zsSuit  = new ZsSuit();

```

    配置
```javascript
    zsSuit.config();
```

    设置层级
```javascript
    zsSuit.set(1, 3);//第二层级，选中了值为3的选项
```

    取消层级设置
```javascript
    zsSuit.unset();
```

    设置回调,名称是插件指定的，不可变
```javascript
    zsSuit.callBack = function(data,skuId){}
```


#使用流程
1.将全部套装数据按照层级关系生成JSON对象
```javascript
    suitRuleInfo             = eval({"123":"1_2_10","234":"1_3_11","345":"2_3_10","456":"3_1_11","789":"4_1_10"});
```

2. 配置已有套装参数
```javascript
    var zsSuit  = new ZsSuit();
    zsSuit.config({'suitRuleInfo':suitRuleInfo});
```

3.设置回调函数，data表示不可选层级，skuId表示确定了唯一套装ID。每一次set或unset操作，都会触发此函数的回调。
```javascript
    zsSuit.callBack = function(data, skuId){
        //不可选处理,i表示层级
        for(var i in data){
            //...
        }
    };
```
        
4.套装选择事件
```javascript
    $("li[fn='click']").click(function(){
        var _self           = $(this),
            chooseFlag      = _self.hasClass("current");
        //取消还是设置
        if(chooseFlag){
            zsSuit.unset(position, curVal);
        }else{
            zsSuit.set(position,curVal);
        }
    });
```

#问题与咨询
使用示例: suit/test.html
个人网址:http://www.noomall.cn
咨询QQ:281-818-570

