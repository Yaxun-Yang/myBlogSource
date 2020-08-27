---
title: "Spring Boot + Mybatis+Vue 初始化配置"
date: 2020-06-14T15:43:47+08:00
draft: false
---
1. 新建项目 
 - new Project -> Spring Initializr(保证 SDK 1.8+)
 - dependencies 选择：
   Developer Tools:Spring Boot DevTools； 热部署
   Web:Spring Web； web相关
   Template Engines: Thymeleaf ；模板
   SQL: MyBatis Framework;MyBatis 数据库框架          MySQL Driver； MySQL 驱动
2. 数据库导入
在`application.properties`中写入配置
```
package org.csu.mypetstore;

import org.mybatis.spring.annotation.MapperScan;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.CrossOrigin;

@SpringBootApplication
@MapperScan("org.csu.mypetstore.persistence")
@CrossOrigin   //表示允许跨域访问
public class MypetstoreApplication {

    public static void main(String[] args) {
        SpringApplication.run(MypetstoreApplication.class, args);
    }

}

```
3. 在src.main.java文件夹下建立`controller`、`domain`、`persistence`、`service`、`more`五个子文件夹
4. 根据配置在resources文件夹下新建mapper目录将所用\*Mapper.xml文件都放在此文件夹下
\*Mapper.xml文件示例
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="org.csu.mypetstore.persistence.CartItemMapper">
<delete id="deleteCartItem">
        DELETE
        FROM CARTITEM
        WHERE CARTID = #{cartId}
        AND   ITEMID = #{itemId}
    </delete>
    <update id="updateQuantity">
        UPDATE CARTITEM
        SET
            QUANTITY = #{quantity}
        WHERE CARTID = #{cartId}
         AND   ITEMiD = #{itemId}
    </update>
</mapper>
```
并在src.java.org.csu.mypetstore.persistence文件夹下建立相应的接口文件\*Mapper
\*Mapper接口文件示例
```
package org.csu.mypetstore.persistence;

import org.csu.mypetstore.domain.Account;
import org.springframework.stereotype.Repository;

@Repository
public interface AccountMapper {
    Account getAccountByUsername(String username);

    Account getAccountByUsernameAndPassword(Account account);

    void insertAccount(Account account);

    void insertProfile(Account account);

    void insertSignOn(Account account);

    void updateAccount(Account account);

    void updateProfile(Account account);

    void updateSignOn(Account account);
}

```

