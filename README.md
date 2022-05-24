# yiri_mirai_qiandao
## 1.安装YiriMiral
![图片](https://user-images.githubusercontent.com/80308986/169965484-3d1cf650-45c9-4e45-a61c-dda9fd0d49e3.png)

pip install yiri-mirai

详细参考https://yiri-mirai.wybxc.cc/docs/intro

## 2.将bot.py放入mcl同级目录下（为了方便寻找插件路径）

## 3.在plugins目录下建立一个pyPlugins文件夹，将qiandao.py放进去

## 4.bot.py配置：

```  
from mirai import Mirai, WebSocketAdapter,GroupMessage

from plugins.pyPlugins import jytime，qiandao#这样的方式引用插件

if __name__ == '__main__':

    bot = Mirai(
    
        qq=123456,#你机器人的qq 
        
        adapter=WebSocketAdapter(
        
            verify_key='12345678', host='localhost', port=8008#这里设置可以看官方文档或者往下看介绍
            
        )
        
    )
    
    qiandao.main(bot)#这玩意要写在bot.run()前面
    
    '''
    
    多个插件就
    
    qiandao.main(bot)
    
    qiandao.main(bot)
    
    jytime.main(bot)...
    
    这样一个个列出来就行
    
    '''
    
    bot.run()
```  
    
## 5.setting.yum

mirai-api-http的配置文件，在config\net.mamoe.mirai-api-http里

配置如下：

```  
adapters:

  - ws
  
debug: false

enableVerify: true

verifyKey: 12345678

singleMode: false

cacheSize: 4096

adapterSettings:

  ws:
  
    host: localhost
    
    port: 8008
    
    reservedSyncId: -1
```  
    
## 把config文件夹放进pyPlugins文件夹
