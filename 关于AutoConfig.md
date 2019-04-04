关于AutoConfig

1. 原始地址： <https://www.baeldung.com/spring-boot-custom-auto-configuration>
2. 配置日志后， 打印出来： <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} ${LOG_LEVEL_PATTERN:-%5p} ${PID:- } --- [%t] %-40.40logger{39}[lineno:%line]: %m%n
   1. 日志内容： ![image-20190404084829413](/Users/wangxichun/Library/Application Support/typora-user-images/image-20190404084829413.png)
   2. DataSourcePoolMetadataProvidersConfiguration类中， 看到这样的代码![image-20190404084959098](/Users/wangxichun/Library/Application Support/typora-user-images/image-20190404084959098.png)
   3. DataSourcePoolMetadataProvidersConfiguration类中有多个DataSourcePoolMetadataProvider的Bean生成配置，每个生成配置中， 都对应地有一个@ConditionalOnClass(XXXX.class). SpringBoot启动时， 据ConditionalOnClass里的Class是否匹配，从而确定具体调用哪个方法， 生成DataSourcePoolMetadataProvider对象。 
3. Spring-Boot带来极大便利的同时， 也带来不小的学习成本和思维方式上的调整：
   1. 不再是显示的。可能会被批为不直观。
   2. 码而优则仕的大背景下，这样的学习成本，很影响SpringBoot的最终落地。
   3. 这方面已有的案例是Hibernate，在国内使用率不高。其背后的原因，有两个：OO的思想不重视， 因自动化特性带来的学习成本及不可控让Hibernate不能落地。
   4. 这也是技术专栏的机会：通过深入系统的研读、整理，一方面方便直接Coder的直观使用，另一方面，也对决策者的思维方式转变起到些许的提升。
4. 