# gitUseTest
简介：
测试脚本模拟真人客户端行为连接斗地主服务器，从而测试服务器潜在的bug。

测试功能请参照流程图：
![Image text](https://github.com/liuaibin/gitUseTest/blob/bil-dev/%20flowChart.png?raw=true)
match模块主要功能：（1）拉取比赛列表选取可报名的比赛。（2）报名比赛（如果有已经报名的比赛则进入比赛）。（3）选取已经报名的并且最近要开赛的场次，进入比赛等待比赛开始。（4）等待比赛结束，退出。
game模块主要功能：（1）拉取房间列表，随机选取可以进入的房间。（2）如果超时没有匹配到人，退出。（3）开始游戏。（4）等待游戏结束。根据一定的概率判断是否退出游戏和继续下一局游戏。
好友桌模块主要功能：（1）拉取好友桌列表信息。

使用流程：
1.配置状态机配置文件，默认包含全部状态。
状态机配置：config目录 ezStates.json
例子：
‘’‘
"Logout": {
    "name":"Logout", //当前状态的名字，一定要和当前状态key一样。
    "delay":[0,5],   //当前状态切换到下个状态的等待时间范围。
    "nextState": [
      {
        "name":"state1",  //下一个状态的名字
        "weight":50       //切换下一个状态所占的权值。
      }，
      {
        "name":"state2",  //下一个状态的名字
        "weight":50       //切换下一个状态所占的权值。
      }
    ]
  }
’‘’
2.配置状态机配置文件，默认包含全部状态。
基本配置： config目录 initConfig.json
例子：
{
  "address":"127.0.0.1",   //服务器的ip
  "port":20200,            //服务器的端口
  "openIdMin":9000020000,  //机器人的openId的起始
  "openIdMax":9000040000,  //机器人的openId的结束
  "clientType":{           //连接类型
    "type":[
      "tcp",
      "websocket"],
    "weight":[             //连接类型权重
      10,
      0
    ]
  },
  "clientNum":100,        //默认客户端的数量
  "agentId":0             //默认的进程id
}
使用流程：
1.修改启动脚本：node ../startClient.js -a "进程id" -c "客户端数量" >> /dev/null 2>&1 &   开启多个进程依次累加进程id
2.开始 => bin目录下 ./start.sh
3.结束 => bin目录下 ./kill.sh

