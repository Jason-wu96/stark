# stark一个便于CRUD的组件

#### 最近学校老师找我和同学做一个项目，关于CRM管理的，以前也做过一些小项目，但都拿不上台面，这次同学们合作，
#### 老师作为指导给小组成员分配任务共同完成CRM管理系统的开发

### Stark组件设计原理
  * 仿django admin的一款实现部分url分支增删改查的操作
 
### 开发环境
* python3.6
* django2.2
-sqlite3(测试用，最好用MySQL)

### 开发目的
* 首先想对自己这段时间的学习进行一次检验，通过这次开发找到自己不足的地方加以改进
* 其次就是想通过这次项目的经验为以后找工作打基础

### 开发流程
#### (1)先建关系表（测试用)
    Book               Publish          Author       AuthorDetail

#### (2)创建stark App  在setting.py中设置添加

#### (3)注册models表
      -1 用到admin源码中的代码
	    -2 单例模式 （site）
	        其中实现单例模式的方法
		        -1 模块
		        -2 __new__方法
		        -3 装饰器
		        -4 元类

#### (4)url设计
	    -url的分发
		    eg: url('^yuan/',([]. None, None)
	    -为了方便在后面使用，给每个URL都设置反向解析（reverse）
        -(小知识）
            1 Book = Book._meta.model_name
            2 app01 = Book._meta.app_label

#### (5)数据展示页面
	    -1构造表单数据
            构造成[
                    ['obj1.name','obj1.price'],
                    ['obj2.name','obj2.price'],
                  ]
		-2用到的知识点
			-1 callable（）是否可被调用
			-2 isinstance（）是否属于哪种方法
			-3 反射
	    -3（小知识）
		    -1 model._meta.get_field(field)
	        -2 构建表头数据
		    -3 checkobox和编辑删除选项运用函数来实现

#### (6)增删改查的实现
	    -运用ModelForm组件完成

#### (7)分页，searc模糊查询，action批量操作
	    -1在分页组件的基础上加上request.GET来实现url保留筛选条件
	    -2 search查询使用ORM的Q查询
		-3 Q查询方式
			1 直接按照字段查找
			2 根据字符串查找
	    -4 action批量操作


