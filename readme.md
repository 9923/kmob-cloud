# 千陌Java开发规范
## 开发手册
- 参考alibaba开发手册pdf，文件在[本地svn](http://192.168.1.5:8443/)的docs/开发文档/阿里巴巴Java开发手册(终极版).pdf位置

## eclipse指导
1. 代码格式化规范使用该项目下eclipse-java-google-style.xml，引入流程如下：

```
graph LR
        A[eclipse]-->B(Windows)
        B --> C(java)
        C --> D(Formatter)
        D --> E(import)
```
2. svn 提交需配置忽略提交以下资源

![image](http://s1.wailian.download/2017/11/18/ignored_resources.png)

添加忽略流程如下：
```
graph LR
        A[eclipse]-->B(Windows)
        B --> C(Team)
        C --> D(Ignored Resource)
        D --> E(Add Pattern)
```

3. java注释规范，只允许使用以下标签，不能使用除这些以外的标记，如@date等

标记 | 说明 | 用于
-----|---|--
@author | 作者标识 | 包、 类、接口
@version  | 版本号 | 包、 类、接口
@since  | API在什么程序的什么版本后开发支持 | 包、类、接口、值域、构造函数、 方法
@param   | 方法的入参名及描述信息，如入参有特别要求，可在此注释 | 构造函数、 方法
@deprecated | 标识随着程序版本的提升，当前API已经过期，仅为了保证兼容性依然存在，以此告之开发者不应再用这个API | 包、类、接口、值域、构造函数、 方法
@throws  | 构造函数或方法所会抛出的异常 | 构造函数、 方法
@see   | 引用 | 包、类、接口、值域、构造函数、 方法
@return   | 对函数返回值的注释 | 方法
@link  | 链接到某个特定的成员对应的文档中 | 包、类、接口、值域、构造函数、 方法
@code  | 版本号 | 包、 类、接口

详细请参考[连接](https://docs.oracle.com/javase/1.5.0/docs/tooldocs/windows/javadoc.html)

4. Git项目导入eclipse流程

```
graph LR
A[eclipse]--> B(import)
B --> C(Git)
C --> D(Projects from Git)
D --> E(Clone URI)
E --> F(import as gernal project)
```

5. 转换为maven项目
```
graph LR
A[project]-->B(configure)
B --> C(convert to maven project)
C --> D(import Existing maven projects)
```

6. 执行安装，直接点击项目中mvnw.cmd即可，这里会下载maven3.1.1的包，如果你电脑本身是3.1.1则不会
7. 执行clean package 会执行生成javadoc，test，开发过程中可以用以下命令跳过这两步

```
-Dmaven.javadoc.skip=true -Dsource.skip -DskipTests clean package 
```

8. 使用代码生成工具生成集成代码
- 下载[代码生成工具项目地址](http://59.110.6.79:10080/zhouzx/beetl-generator.git)
- 修改配置文件resources/conf目录下db.properties为数据库配置，template.properties为代码模版生成配置，具体配置
详细看配置文件注释
- 执行GeneratorStart类，生成的代码路径为output目录。
