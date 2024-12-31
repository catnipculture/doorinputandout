> #### 作者主页：[舒克日记](https://blog.csdn.net/cativen)
>
>  简介：Java领域优质创作者、Java项目、学习资料、技术互助
>
> <b><font color=red>文中获取源码</font></b>

## 前言

本java的防盗门进销存系统主要完成对防盗门的管理，

包括库存管理、订单审核、采购管理、销售管理、账户管理、统计分析等几个方面。

​

系统可以完成对各类信息的浏览、查询、添加、删除、修改等功能。

系统采用了jsp的mvc框架,SSM(springMvc+spring+Mybatis)框架进行开发,本系统是独立的运行，不依附于其他系统，可移植，可扩展。代码的编写规范，注解较多，同时也是计算机毕业设计中一项重要的参考资料等。

# 技术栈

后台框架：Spring、SpringMVC、MyBatis

数据库：MySQL

环境：JDK8、TOMCAT、IDEA

# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq 

源码地址：[http://www.codegym.top](http://www.codegym.top/)

### 数据库设计

![微信图片20240928230013](https://img-blog.csdnimg.cn/img_convert/1ed633612281fe9fbe0d069ca16fa11b.png)

###

### 运行截图

### 登录页

![68747470733a2f2f692e6c6f6c692e6e65742f323031392f30382f31362f6a7747634d424f7a394335555338412e706e67](https://img-blog.csdnimg.cn/img_convert/8bbee8b0deb18f2f46ed200ce1bdd1d5.png)

####

#### 系统主页

![68747470733a2f2f692e6c6f6c692e6e65742f323031392f30382f31362f4d6f5039564f7441313873514e45482e706e67](https://img-blog.csdnimg.cn/img_convert/b7659c3ee9ef47e3f589d72531fe6782.png)

####

#### BootStrap风格

![68747470733a2f2f692e6c6f6c692e6e65742f323031392f30382f31362f6c4c66384f76316842705a465053592e706e67](https://img-blog.csdnimg.cn/img_convert/e81ba08c3cd8d3c1eb0ca2ce20c32f9d.png)

####

#### Echarts数据可视化


### 代码

```
    public String getTenantNameByUserId(String userId) {
        if (RequestUtils.isAdministrator()) {
            //查询所有的租户信息
            List<UserTenancyDO> userTenancyByUserId = getUserTenancyByUserId(userId);
            if (CollectionUtils.isEmpty(userTenancyByUserId)) {
                return "";
            } else {
                return userTenancyByUserId.stream()
                        .map(UserTenancyDO::getTenantName) // 将每个UserTenancyDO映射到其tenantName
                        .collect(Collectors.joining(","));
            }
        } else {
            //查询当前用户的租户信息
            UserTenancyDO userTenancyByUserIdAndTenantId = getUserTenancyByUserIdAndTenantId(userId, RequestUtils.getCurrentTenantId());
            return userTenancyByUserIdAndTenantId.getTenantName();
        }
    }
```
