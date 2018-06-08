# 实验4：图书管理系统顺序图绘制
|学号|班级|姓名|
|:-------:|:-------------: | :----------:|
|201510414316|软工2015-3|王壮|

## 图书管理系统的顺序图

## 1. 图书批量增删用例
## 1.1 图书批量增删用例PlantUML源码
```
@startuml
skinparam sequenceParticipant underline

actor 二级管理员
participant "图书馆主页" as A
participant "图书管理" as B
participant "图书" as C
participant "管理员" as D

二级管理员-->A:登录系统
activate A
A-->D:验证管理员信息
activate D
deactivate D
A -> B:进入系统功能
activate B
B -> C:读取所有图书信息
activate C
B -> C:更新图书
C -> B:更新成功
deactivate C
B -> A:返回主页
deactivate B
A -> 二级管理员:注销登录
deactivate A
@enduml
```

## 1.2 图书批量增删顺序图
![](./Image001.png '描述')

## 1.3 图书批量增删说明
    二级管理员首先登录系统，登陆成功后，选择图书批量增删功能，对图书进行批量操作，保存更改，返回系统，注销登录。

## 2. 一级管理员管理用例
## 2.1 一级管理员管理用例PlantUML源码
```
@startuml
skinparam sequenceParticipant underline

actor 二级管理员
participant "图书馆主页" as A
participant "一级管理员管理" as B
participant "管理员" as C

二级管理员-->A:登录系统
activate A
A --> C:验证二级管理员信息
activate C
A -> B:进入系统功能
activate B
B -> C:读取所有一级管理员信息
B -> C:更新管理员信息
C -> B:更新成功
deactivate C
B -> A:返回主页
deactivate B
A -> 二级管理员:注销登录
deactivate A
@enduml
```

## 2.2 一级管理员管理用例顺序图
![](./Image002.png '描述')

## 2.3 一级管理员管理用例说明
    二级管理员首先登录系统，登陆成功后，选择管理员功能，对一级管理员进行操作，保存更改，返回系统，注销登录。

## 3. 读者管理用例
## 3.1 读者管理用例PlantUML源码
```
@startuml
skinparam sequenceParticipant underline

actor 二级管理员
participant "图书馆主页" as A
participant "读者管理" as B
participant "读者" as C
participant "管理者" as D

二级管理员-->A:登录系统
activate A
A --> D:验证二级管理员信息
activate D
deactivate D
A -> B:进入系统功能
activate B
B -> C:读取所有一级读者信息
activate C
B -> C:更新读者信息
C -> B:更新成功
deactivate C
B -> A:返回主页
deactivate B
A -> 二级管理员:注销登录
deactivate A
@enduml
```

## 3.2 读者用例顺序图
![](./Image003.png '描述')

## 3.3 读者用例说明
    二级管理员首先登录系统，登陆成功后，选择读者管理功能，对读者进行操作，保存更改，返回系统，注销登录。

## 4. 借书用例
## 4.1 借书用例PlantUML源码
```
@startuml
skinparam sequenceParticipant underline

actor 一级管理员
participant "借书" as A
participant "图书" as B
participant "借书记录" as C

activate 一级管理员
一级管理员-->A:进入功能
activate A
A -> B:查找相对图书信息
activate B
A --> B:减少图书数量
A --> C:增加借书记录
activate C
deactivate C
B --> A:借阅成功
deactivate B
A --> 一级管理员:返回主页
deactivate A
deactivate 一级管理员
@enduml
```

## 4.2 借书用例顺序图
![](./Image004.png '描述')

## 4.3 借书用例说明
    省略了登录系统步骤，一级管理员选择借书功能，增加借书信息，保存，返回系统。

## 5. 查询图书用例
## 5.1 查询图书用例PlantUML源码
```
@startuml
skinparam sequenceParticipant underline

actor 一级管理员或读者
participant "查询图书" as A
participant "图书" as B

activate 一级管理员
一级管理员-->A:进入功能
activate A
A -> B:查找相应图书信息
activate B
B --> A:返回相应图书信息
deactivate B
A --> 一级管理员:返回主页
deactivate A
deactivate 一级管理员
@enduml
```

## 5.2 查询图书用例顺序图
![](./Image005.png '描述')

## 5.3 查询图书用例说明
    省略了登录系统步骤，一级管理员或者读者选择查询图书功能，选择查询条件，搜索，查看搜索结果，返回系统。

## 6. 还书用例
## 6.1 还书用例PlantUML源码
```
@startuml
skinparam sequenceParticipant underline

actor 一级管理员
participant "还书" as A
participant "借书记录" as B
participant "图书" as C

activate 一级管理员
一级管理员-->A:进入功能
activate A
A -> B:查找相对借书信息
activate B
A --> C:增加图书数量
activate C
deactivate C
A --> B:删除借书记录
B --> A:归还成功
deactivate B
A --> 一级管理员:返回主页
deactivate A
deactivate 一级管理员
@enduml
```

## 6.2 还书用例顺序图
![](./Image006.png '描述')

## 6.3 还书用例说明
    省略了登录系统步骤，一级管理员选择还书功能，删除借书信息，增加图书数量，保存，返回系统。

## 7. 罚款查询用例
## 7.1 罚款查询用例PlantUML源码
```
@startuml
skinparam sequenceParticipant underline

actor 一级管理员或读者
participant "罚款查询" as A
participant "借书记录" as B
participant "读者" as C

activate 一级管理员或读者
一级管理员或读者 -->A:进入功能
activate A
A -> C:查找相应读者信息
activate C
deactivate C
A -> B:读者ID在借书记录中进行检索
activate B
B --> A:返回相应记录信息
deactivate B
A --> 一级管理员或读者:根据规则进行处罚
deactivate A
deactivate 一级管理员或读者
@enduml
```

## 7.2 罚款查询用例顺序图
![](./Image007.png '描述')

## 7.3 罚款查询用例说明
    省略了登录系统步骤，一级管理员选罚款查询功能，先查找相对的读者信息，再在借阅表中进行检索，返回检索结果，根据结果进行处罚，返回系统。