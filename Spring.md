## Introduction
فریم ورک spring  یک فریم ورک متن باز برای ساخت و توسعه بهتر و سریع تر نرم افزارهای enterprise بر مبنای JVM می باشد.
دلایل استفاده این همه برنامه نویس از این فریمورک performance بسیار بالا و تست راحت و معماری آن است.
هدف فریمورک spring این است که برنامه نویسی J2EE را آسان تر کند و با استفاده از مدل برنامه نویسی   **POJO**، برنامه نویسی را گسترش دهد.

هدف اصلی این فریم ورک نرم افزارهای enterprise مانند سیستم های اطلاعاتی ERP می باشد.اما در موارد دیگر مانند app های موبایل و سیستم های cload هم از spring استفاده می شود. 
## Architecture 
![architecture](https://user-images.githubusercontent.com/34265067/236350881-578a0ee7-04fd-4492-aa1b-894e9bf161de.png)

فریم ورک spring برای همه لایه ها از UI گرفته تا data access و core راهکار دارد.
### Core Container :
-  Core : IOC and DI features
- Bean : BeanFactory container
- Cpntext : ApplicationContextContainer
- SpEL : Spring expression language

## Setting Up
**مراحل نصب  :**
1. Install last version of JDK ( download from [oracle](https://www.oracle.com/))
2. set environment variables(set **JAVA_HOME** system variable and add it to **path** variable) . Now check **java -version** command in cmd for success installation of JDK.
3. Install an IDE (e.g intellij , Netbeans , Eclipse and etc.) . Netbeans ans Eclipse is much better. Eclipse is oopen sourse. The rest of the settings up is based on Eclipse Neon.
4. Install a DBMS (e.g Mysql , Oracle (not free) , PostgreSQL) . We use PostgreSQL as it`s free and high ranking.
## IOC
