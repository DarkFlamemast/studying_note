## actionlmpl()

#### update strategy and anaylizer

> **Strategy::instance().update() **包含**UpdateSituation**和**UpdatePosition**两部分



#### create the role

**Strategy::i().createRole(int unum,  const rcsc::WorldModel &wm )**

在createRole中：

**Formation::Ptr f = Getformation(world) **   获取当前阵型

**f->getRoleName(int unum)**      根据阵型分配role











## situation

gamemode != playon

- PenaltyKick   点球

- OurSetPlay    我方任意球
- OppSetPlay    敌方任意球

gamemode == playon

- Defence  (opp_min <= our_min - 2)
- Offence   (our_min <= opp_min - 1)





## roletype

- goalie 守门员
- centerback 中后卫
- sideback 边后卫
- defensivehalf 防守中卫
- offensivehalf  进攻中卫
- sidehalf 中边卫
- sideforward 边锋
- centerforward 前中锋

