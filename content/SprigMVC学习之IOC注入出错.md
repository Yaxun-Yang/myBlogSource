---
title: "SprigMVC学习之IOC注入出错"
date: 2020-03-13T20:04:06+08:00
draft: false
Tags:
- SpringMVC
- 课程学习
- 笔记
- 坑
---

## 背景
初学SpringMVC 尝试使用标签代替xml配置，然后报错，完整报错如下：
```
"C:\Program Files\Java\jdk1.8.0_91\bin\java.exe" -ea -Didea.test.cyclic.buffer.size=1048576 "-javaagent:D:\download\IntelliJ IDEA 2019.2.2\lib\idea_rt.jar=55492:D:\download\IntelliJ IDEA 2019.2.2\bin" -Dfile.encoding=UTF-8 -classpath "D:\download\IntelliJ IDEA 2019.2.2\lib\idea_rt.jar;D:\download\IntelliJ IDEA 2019.2.2\plugins\junit\lib\junit5-rt.jar;D:\download\IntelliJ IDEA 2019.2.2\plugins\junit\lib\junit-rt.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\charsets.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\deploy.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\access-bridge-64.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\cldrdata.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\dnsns.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\jaccess.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\jfxrt.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\localedata.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\nashorn.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\sunec.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\sunjce_provider.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\sunmscapi.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\sunpkcs11.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\ext\zipfs.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\javaws.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\jce.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\jfr.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\jfxswt.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\jsse.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\management-agent.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\plugin.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\resources.jar;C:\Program Files\Java\jdk1.8.0_91\jre\lib\rt.jar;D:\java\springDemo\springDemo\target\classes;C:\Users\87911\.m2\repository\junit\junit\4.11\junit-4.11.jar;C:\Users\87911\.m2\repository\org\hamcrest\hamcrest-core\1.3\hamcrest-core-1.3.jar;C:\Users\87911\.m2\repository\org\springframework\spring-core\5.2.3.RELEASE\spring-core-5.2.3.RELEASE.jar;C:\Users\87911\.m2\repository\org\springframework\spring-jcl\5.2.3.RELEASE\spring-jcl-5.2.3.RELEASE.jar;C:\Users\87911\.m2\repository\org\springframework\spring-beans\5.2.3.RELEASE\spring-beans-5.2.3.RELEASE.jar;C:\Users\87911\.m2\repository\org\springframework\spring-expression\5.2.3.RELEASE\spring-expression-5.2.3.RELEASE.jar;C:\Users\87911\.m2\repository\org\springframework\spring-context\5.2.3.RELEASE\spring-context-5.2.3.RELEASE.jar;C:\Users\87911\.m2\repository\org\springframework\spring-aop\5.2.3.RELEASE\spring-aop-5.2.3.RELEASE.jar" com.intellij.rt.junit.JUnitStarter -ideVersion5 -junit4 org.csu.springDemo.ioc.test.AccountDemo,test
三月 13, 2020 1:39:17 下午 org.springframework.context.support.AbstractApplicationContext refresh
警告: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'account' defined in file [D:\java\springDemo\springDemo\target\classes\org\csu\springDemo\ioc\domain\Account.class]: Unsatisfied dependency expressed through constructor parameter 0; nested exception is org.springframework.beans.factory.NoSuchBeanDefinitionException: No qualifying bean of type 'java.lang.String' available: expected at least 1 bean which qualifies as autowire candidate. Dependency annotations: {}

org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'account' defined in file [D:\java\springDemo\springDemo\target\classes\org\csu\springDemo\ioc\domain\Account.class]: Unsatisfied dependency expressed through constructor parameter 0; nested exception is org.springframework.beans.factory.NoSuchBeanDefinitionException: No qualifying bean of type 'java.lang.String' available: expected at least 1 bean which qualifies as autowire candidate. Dependency annotations: {}

	at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:798)
	at org.springframework.beans.factory.support.ConstructorResolver.autowireConstructor(ConstructorResolver.java:228)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.autowireConstructor(AbstractAutowireCapableBeanFactory.java:1358)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1204)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:557)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:517)
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:323)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:321)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:879)
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:878)
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:550)
	at org.springframework.context.support.ClassPathXmlApplicationContext.<init>(ClassPathXmlApplicationContext.java:144)
	at org.springframework.context.support.ClassPathXmlApplicationContext.<init>(ClassPathXmlApplicationContext.java:85)
	at org.csu.springDemo.ioc.test.AccountDemo.test(AccountDemo.java:17)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.junit.runners.model.FrameworkMethod$1.runReflectiveCall(FrameworkMethod.java:47)
	at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:12)
	at org.junit.runners.model.FrameworkMethod.invokeExplosively(FrameworkMethod.java:44)
	at org.junit.internal.runners.statements.InvokeMethod.evaluate(InvokeMethod.java:17)
	at org.junit.runners.ParentRunner.runLeaf(ParentRunner.java:271)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:70)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:50)
	at org.junit.runners.ParentRunner$3.run(ParentRunner.java:238)
	at org.junit.runners.ParentRunner$1.schedule(ParentRunner.java:63)
	at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:236)
	at org.junit.runners.ParentRunner.access$000(ParentRunner.java:53)
	at org.junit.runners.ParentRunner$2.evaluate(ParentRunner.java:229)
	at org.junit.runners.ParentRunner.run(ParentRunner.java:309)
	at org.junit.runner.JUnitCore.run(JUnitCore.java:160)
	at com.intellij.junit4.JUnit4IdeaTestRunner.startRunnerWithArgs(JUnit4IdeaTestRunner.java:68)
	at com.intellij.rt.junit.IdeaTestRunner$Repeater.startRunnerWithArgs(IdeaTestRunner.java:33)
	at com.intellij.rt.junit.JUnitStarter.prepareStreamsAndStart(JUnitStarter.java:230)
	at com.intellij.rt.junit.JUnitStarter.main(JUnitStarter.java:58)
Caused by: org.springframework.beans.factory.NoSuchBeanDefinitionException: No qualifying bean of type 'java.lang.String' available: expected at least 1 bean which qualifies as autowire candidate. Dependency annotations: {}
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.raiseNoMatchingBeanFound(DefaultListableBeanFactory.java:1695)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1253)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1207)
	at org.springframework.beans.factory.support.ConstructorResolver.resolveAutowiredArgument(ConstructorResolver.java:885)
	at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:789)
	... 37 more


Process finished with exit code -1


```
## 解决方案和原因
问题出在在有构造方法的前提下仅仅完成set注入，这个故事告诉我们，构造注入的优先级高于set注入，在有构造方法的前提下一定要构造注入。