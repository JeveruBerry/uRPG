
# 地形地貌系统

大世界由若干六边形网格组成，每个网格有自己的地形地貌特征。

## 地形

基本地形有平原、草原、荒漠、冻土、雪原、山脉6种

以上基本地形按照平坦和崎岖不同又可分别划分为两类，那就是：

- 平原平地（1粮1锤）
- 平原丘陵（2锤）
- 草原平地（2粮）
- 草原丘陵（2锤）
- 荒漠平地（0）
- 荒漠丘陵（2锤）
- 冻土平地（1粮）
- 冻土丘陵（2锤）
- 雪原平地（0）
- 雪原丘陵（0）

另外，山脉是作为不可移动的地形存在

## 地貌

地貌就是地面附着物，主要有森林、丛林、沼泽、冲击平原、绿洲等类型

跟地形关联生成，如：

- 丛林在平原、冲积平原
- 绿洲在沙漠
- 沼泽在草原

抹除原地形产出，当清除地貌时，恢复原地形产出。地貌产出如下：

- 森林（1粮1锤）
- 丛林（2粮）
- 沼泽（1粮）
- 冲击平原（2粮）
- 绿洲（3粮1金），绿洲没有对应的清除地貌的科技，所以除了坐城外无法抹除，坐城后清除绿洲效果，变为普通荒漠

## 资源产出

资源分为`奖励`、`战略`和`奢侈`三类
资源产出均是在地形产出和地貌产出的基础上直接加成一定的产出

奖励资源:基本都是+1粮（花岗石除外，+1锤）：小麦、鹿、香蕉、牛、羊

战略资源:基本都是+1锤：马、铁、铝、煤、石油、铀

奢侈资源:基本都是+2金，宝石+3金，盐、柑橘（海产中的螃蟹、鲸鱼）+1粮1金

## 改良设施

所谓改良设施就是工人在地形或资源上建造相应的设施，如：

- 在平地上建农田
- 在丘陵上建矿井
- 在森林里建伐木场

需要注意的是，改良设施产出包括两方面，第一个是设施本身加成（即不针对资源的），如：

- 农场+1粮
- 矿井、伐木场、采石场+1锤
- 贸易站+1金等

第二个则是资源改良加成，如：

- 马、牛建立牧场+1锤
- 羊建立牧场则+1粮
- 大多数奢侈改良后+1金
- 盐改良后会+1粮不+金
- 平原平地盐改良后产出为平原平地（1粮1锤）+盐加成（1粮1金）+矿井加成（1锤）+资源改良加成（1粮）=3粮2锤1金