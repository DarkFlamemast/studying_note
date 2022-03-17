\# 怎么写代码

\```cpp
\#ifdef HAVE_CONFIG_H
\#include <config.h>
\#endif

\#include <rcsc/action/basic_actions.h>
\#include <rcsc/action/body_go_to_point.h>
\#include <rcsc/action/neck_scan_field.h>
\#include <rcsc/action/neck_turn_to_ball_or_scan.h>
\#include <rcsc/common/logger.h>
\#include <rcsc/common/server_param.h>
\#include <rcsc/player/player_agent.h>

\#include "bhv_go_to_moving_ball.h"
\#include "bhv_set_play.h"

using namespace rcsc;

/*-------------------------------------------------------------------*/
/*!

*/
bool Bhv_GoToMovingBall::execute(PlayerAgent* agent) {
 const WorldModel& wm = agent->world();
 if (wm.ball().posValid()) {
  agent->doDash(ServerParam::i().maxDashPower(), wm.ball().angleFromSelf());
  agent->setNeckAction(new Neck_TurnToBall());
 } else {
  agent->setNeckAction(new Neck_TurnToBallOrScan(0));
 }
 return true;
}
\```



\## 如何获取场上的情况？

\### 球员`agent`

它所获取的场上情况都在`WorldModel`中。

`WorldModel`中的主要信息

\- ball
\- self

`self`中的主要信息

\- angleFromBall
\- body
\- vel
\- dist
\- distFromBall
\- playerTpe
 \- kickableArea()
 \- playerSize()

`ball`中的主要信息

\- pos
\- posValid
\- posCount
\- vel
\- angleFromSelf

\### 默认的设置

```
ServerParam::i()
```

\- ServerParam::i().defaultKickableArea()
\- wm.self().playerType().kickableArea()

\## 如何做动作？

\### 原子化的操作`agent->do*`

\- ~~agent->doMove~~
\- agent->doDash
\- agent->doTurn
\- agent->doTurnNeck
\- ...

一个周期能完成的动作有限制

\### 高级动作`Body_*`

位于`rcsc/action/*`

\- Body_GoToBall
\- Body_TurnToBall
\- Body_TurnToPoint

脖子的动作

```
agent->setNeckAction(new Neck*)
```

\- Neck_TurnToBallOrScan

\### 动作限制

冲刺加速限制

\- wm.self().playerType().playerSpeedMax()
\- wm.self().playerType().realSpeedMax()
\- wm.self().getSafetyDashPower()
\- ServerParam::i().maxDashPower()
\- ServerParam::i().defaultPlayerSpeedMax()
\- ServerParam::i().ballDecay()

关于速度的模型：<![img](file:///C:\Users\Ricardo\AppData\Roaming\Tencent\QQTempSys\%W@GJ$ACOF(TYDYECOKVDYB.png)https://rcsoccersim.readthedocs.io/en/latest/soccerserver.html#dash-model>