# 数据库设计 [首页](./README.md)

<div id="USERS"></div>

- ## USERS表（用户表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |USER_ID|NUMBER(8,0)|主键|否| | | 用户ID|
    |NAME|VARCHAR2(50 BYTE)| |否| | | 用户真实姓名|
    |GITHUB_USERNAME|VARCHAR2(50 BYTE)| |是|空| | GitHUB用户名|
    |UPDATE_DATE|DATE| |是|空| | GitHUB用户名修改日期|
    |PASSWORD|VARCHAR2(512 BYTE)| |是|空| | 加密存储密码，为空表示密码就是学号|
    |DISABLE|VARCHAR2(20 BYTE)| |否| | |是否禁用,值为是表示禁用,其他表示正常.|

<div id="TEACHERS"></div>

- ## TEACHERS表（老师表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |TEACHER_ID|VARCHAR2(50 BYTE)|主键|否| | | 老师的编号|
    |USER_ID|NUMBER(8,0)|外键|是| | | 老师的用户ID，USERS表的外键|
    |TEACHER_NAME|VARCHAR(20 BYTE)| |否| | | 老师的姓名|
    |DEPARTMENT|VARCHAR2(400 BYTE)| |否| | | 老师属于的部门|

<div id="STUDENTS"></div>

- ## STUDENTS表（学生表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |STUDENT_ID|VARCHAR2(50 BYTE)|主键|否| | | 学生的学号|
    |USER_ID|NUMBER(8,0)|外键|是| |空| 学生的用户ID，USERS表的外键，为空表示还没有建立用户|
    |CLASS|VARCHAR2(20 BYTE)| |否| | | 学生的班级|
    |RESULT_SUM|VARCHAR2(400 BYTE)| |是|空| | 成绩汇总（来自GRADES表），每次实验成绩的平均分|
    |WEB_SUM|VARCHAR2(400 BYTE)| |是|空| | GitHub网址是否正确，用逗号分开，Y代表正确，N代表不正确。|


<div id="TIMETABLE"></div>

- ## TIMETABLE表（课程库表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |COURSE_NAME|VARCHAR2(50 BYTE)|联合主键1|否| | | 课程名称|
    |SEMESTER|VARCHAR2(50 BYTE)|联合主键2|否| | | 学期|
    |COURSE_NUMBER|NUMBER(6,0)| |否| | |安排上课人数|
    |S_NUMBER|NUMBER(6,0)| |是|0| |已选人数，当满时学生不能再选课|
    |SELECT_TEACHER|VARCHAR2(50 BYTE)|无|是| | |若没有老师选此课，学生不能选择|
    |IS_SELECT|VARCHAR2(20 BYTE)| |否|是| | 学生是否能选|
    |COURSE_ID|VARCHAR2(400 BYTE)| |否| | | 课程代码|
    |COURSE_CREDIT|VARCHAR2(400 BYTE)| |否| | | 课程学分|
    |TEST1|VARCHAR2(400 BYTE)| |是|空| | 学期课程安排的实验|
    |TEST2|VARCHAR2(400 BYTE)| |是|空| | 学期课程安排的实验|
    |TEST3|VARCHAR2(400 BYTE)| |是|空| | 学期课程安排的实验|
    |TEST4|VARCHAR2(400 BYTE)| |是|空| | 学期课程安排的实验|
    |TEST5|VARCHAR2(400 BYTE)| |是|空| | 学期课程安排的实验|

<div id="GRADES"></div>


- ## GRADES表（学生实验成绩表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |GRADES_ID|VARCHAR2(50 BYTE)|主键|否|1| | 成绩表自增主键|
    |COURSE|VARCHAR2(50 BYTE)| |否| | | 课程名|
    |TEST_ID|VARCHAR2(50 BYTE)| |否| | | 实验编号|
    |STEDENT_ID|VARCHAR2(50 BYTE)| |否| | | 学生学号|
    |SEMESTER|VARCHAR2(50 BYTE)| |否| | | 学期|
    |STUDENT_NAME|VARCHAR2(50 BYTE)| |否| | | 学生姓名|
    |TEACHER_NAME|VARCHAR2(50 BYTE)| |否| | | 评分老师|
    |GRADE1|NUMBER(6,0)| |否| | | 实验评分项|
    |GRADE2|NUMBER(6,0)| |否| | | 实验评分项|
    |GRADE3|NUMBER(6,0)| |否| | | 实验评分项|
    |GRADE4|NUMBER(6,0)| |否| | | 实验评分项|
    |GRADE5|NUMBER(6,0)| |否| | | 实验评分项|
    |MEMO|VARCHAR2(400 BYTE)| |是|空| | 老师对实验的评语|
    |UPDATE_DATE|DATE| |否| | |老师批改实验的日期，为空表示未批改|

<div id="SCHEDULES"></div>

- ## SCHEDULES表（学生已选课表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |SCHEDULES_ID|NUMBER(10,0)|主键|否|1| | 已选课表自增主键|
    |STUDENT_ID|VARCHAR2(100 BYTE)| |否| | | 学号|
    |STUDENT_NAME|VARCHAR2(100 BYTE)| |否| | | 学生姓名|
    |S_COURSE|VARCHAR2(100 BYTE)| |否| | | 课程记录|