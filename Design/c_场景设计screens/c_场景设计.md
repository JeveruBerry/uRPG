# 场景设计

目前游戏由4个场景组成，分别是：
- 测试场景
- 登录场景
- 选人场景（暂不制作）
- 主场景

## 数据驱动

场景需要进行一定的数据驱动，比如场景之间的跳转等
为此需要一个数据表，表格需要如下字段

- ID        string
- 场景文件名 string
- 跳转场景ID string
