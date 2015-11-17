# fis-postporcessor-ssi 

## 说明

由于项目中有用到apache 自带的ssi功能，所以需要将`<!--#include virtual="path/to/file(.css|js|html)"-->`引入的内容内嵌进html中。

## 特性
修复原版include页面没替换资源地址的问题

## 使用

先安装

> npm install -g fis-postprocessor-ssi2

配置

	//可以自定义include的正则，如果不需要自定义的话，则忽略这些配置则可
	fis.config.merge({
        settings :{
            postprocessor : {
                'ssi' : {
                    reg : /<!--#include\svirtual="([^"]+)"\s*-->/gim
                }
            }
        }
    });
    
    //设置文件处理类型
	fis.config.merge({
    	modules :{
        	postprocessor : {
            	html : 'ssi',
            	css : 'ssi',
            	js : 'ssi'
        	}
    	}
	});

## FIS3用法
```
fis.match('*.{html,shtml}', {
    postprocessor: fis.plugin('ssi',{
        'ssi' : {
            reg : /<!--#include\svirtual="([^"]+)"\s*-->/gim
        }
    })
});
```