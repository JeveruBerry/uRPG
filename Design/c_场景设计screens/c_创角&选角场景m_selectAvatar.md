# 新建&选择角色

## 设计目的

- 玩家对游戏中扮演的角色的初步DIY：包括属性能力Build和外观修改两部分；
- 玩家可以对自己的角色的外形进行调整，包括各种组件颜色及大小、形状等；
- 玩家可以对属性能力进行选择：
    - 种族选择：初始选择后不可修改；
    - 性别选择：初始选择后不可修改；
    - 职业选择：游戏中的职业概念是模糊的，官方提供的职业只作为预设模板存在。玩家具体的职业取决于玩家在游戏中的属性、天赋和能力的选择；
- 在新建角色过程中传达游戏世界观及相关的玩法规则设定
- 此过程中交由玩家选择的选项不能太过复杂

## 场景初始化

- 请求数据库`获取账号角色信息`流程
- 场景中的BP_selectedAvatar默认存在，且为单例。
- 根据服务器回调事件返回的数据，判断：
    - 若角色数<=0，则打开`新建角色界面`
    - 若角色数>0，则打开`选择角色界面`

## 获取账号角色信息流程

在获取账号信息后，服务器将当前账号的所有角色信息返回，包括：

- 角色ID
- 角色名
- 其他

## 新建角色界面

在新建角色界面中，玩家可以对一下信息进行自定义：

    - 角色种族
    - 角色外形自定义（约5项，详见外形自定义文档）
    - 角色名称
点击`后退`按钮返回“选择角色界面”
点击`同意`按钮进入“创建角色流程”

## 创建角色流程

在新建角色界面中，点击“同意”按钮开始创建角色流程

首先，客户端进行判断：

- 判断角色名是否为空
- 判断角色名是否符合规范
- 判断当前角色数量是否超上限
- 将角色名、种族ID发送给服务器，进行创建角色请求

服务器接收到数据后进行操作：

- 判断角色名是否为空
- 判断角色名是否符合规范
- 判断角色名是否为服务器唯一的
- 判断当前角色数量是否超上限
- 根据角色名、种族ID读取配置表，根据配置数据初始化角色并存入服务器
- 完成创建，回调客户端对应方法（事件）

客户端接收到`创建角色完成`事件后，继续操作：

- 使用当前角色，请求服务器`进入游戏`流程

## 选择角色界面

根据服务器获取的`角色列表`信息，初始化界面上的角色列表，并默认选中**第一项**
玩家可以点选列表中角色，将其设为`选中角色`
`选中角色`是唯一的
点击进入世界按钮，进行`进入游戏`流程

## 进入游戏流程

选择一个角色之后可以进行进入游戏流程

- 根据数据库中保存数据，在服务器实例化角色
- 服务器实例化角色成功后，调用客户端回调事件
- 客户端接收到回调事件后，在客户端实例化角色，并跳转到游戏主场景

## 服务器回调函数

### 删除角色响应事件

成功删除角色，更新角色列表

### 创建角色响应事件

成功创建角色，根据角色信息进入游戏世界

### 进入游戏响应事件

根据选择角色数据，进入游戏世界
