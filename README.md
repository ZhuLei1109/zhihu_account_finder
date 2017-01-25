# zhihu_account_finder
知乎账号查找助手

# 简介
此工具通过取两个赞同列表的交集来辅助定位知乎账号，没办法，在追的妹子，说找到知乎账号有奖～
一般情况下比较两组基本就可以唯一确定，简单改造也可以同时比较多组。

#Step-0 sh init.sh
建立几个空目录

#Step-1 信息收集阶段
线上线下各种方式，获取至少两个收藏或转发，常人在此行为前会触发赞同。

#Step-2 获取回答的赞同列表
打开一个知乎页面，并打开控制台，复制脚本`console/fetchAgree.js`的内容到控制台。
执行方法，示例：`fetchAgree(50688411, 'local001:8084')`
其中`50688411`是回答id，很容易可以获取，`local001:8084`是本地server，用于将抓取的数据发送本地。
由于知乎已经https化，所以本地server需要开启ssl，并且需要添加CORS跨域头，证书签名不熟悉的话可以借助[gencert.sh](https://github.com/michaelliao/itranswarp.js/blob/master/conf/ssl/gencert.sh)生成，如果你用的是nginx，可以参考`nginx.conf.sample`，10000行的列表，数据量大概在3M，post数据大小限制需要修改一下，想象下我跑了10分钟，看到http413的表情，还好chrome的xhr可以replay。

#Step-3 比较列表
此刻我认为你的data/fetch目录下已经存在了两个json文件，假设两个回答的id是22222和33333，访问/compare.php?22222_33333即可，运行完成即可看到结果链接

#Step-4 人肉筛选
一般前期选择合适，比如两个1000赞同的列表，重合度的量级很可观，再结合其他信息，就可以定位知乎账号了。如果一次不行就多选几组。

最后，祝天下有情人终成眷属～



