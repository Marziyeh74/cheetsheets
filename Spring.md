## 1- Introduction
فریم ورک spring  یک فریم ورک متن باز برای ساخت و توسعه بهتر و سریع تر نرم افزارهای enterprise بر مبنای JVM می باشد.
دلایل استفاده این همه برنامه نویس از این فریمورک performance بسیار بالا و تست راحت و معماری آن است.
هدف فریمورک spring این است که برنامه نویسی J2EE را آسان تر کند و با استفاده از مدل برنامه نویسی   **POJO**، برنامه نویسی را گسترش دهد.

هدف اصلی این فریم ورک نرم افزارهای enterprise مانند سیستم های اطلاعاتی ERP می باشد.اما در موارد دیگر مانند app های موبایل و سیستم های cload هم از spring استفاده می شود. 
## 2- Architecture 
![architecture](https://user-images.githubusercontent.com/34265067/236350881-578a0ee7-04fd-4492-aa1b-894e9bf161de.png)

فریم ورک spring برای همه لایه ها از UI گرفته تا data access و core راهکار دارد.
### Core Container :
-  Core : IOC and DI features
- Bean : BeanFactory container
- Cpntext : ApplicationContextContainer
- SpEL : Spring expression language

## 3- Setting Up

1. Install last version of JDK ( download from [oracle](https://www.oracle.com/))
2. set environment variables(set **JAVA_HOME** system variable and add it to **path** variable). Now check **java -version** command in cmd for success installation of JDK.
3. Install an IDE (e.g intellij , Netbeans , Eclipse and etc.). Netbeans ans Eclipse is much better. Eclipse is oopen sourse. The rest of the settings up is based on Eclipse Neon.
4. Install a DBMS (e.g Mysql , Oracle (not free) , PostgreSQL). We use PostgreSQL as it`s free and high ranking. ( download  [PostgreSQL](https://www.postgresql.com/))
5. Install a Web server(e.g Apache Tomcat). We use Tomcat (8.0.37).
    -  unzip Tomcat file in window driver
    - add it to eclipse 
      - menue Window -> show view -> other -> tyoe server and select it.
      - define a new server from the link in tab server (select Tomcat, server hostname and name and then select Apache Tomcat installation folder and select jdk instalation folder for JRE) 
    - test Tomcat server


## 4- IoC(Inversion of Control)

سیستم های اطلاعاتی از یک سری اجزا یا به اصطلاح کامپوننت تشکیل شده اند. این کامپوننت ها یک سری سرویس دارند. اگر بخواهیم اصول مهندسی نرم افزار را رعایت کنیم باید برای هر سرویس یک **Interface** ایجاد کنیم. **Interface** یک بدنه خالی است که باید پیاده سازی شود. ممکن است برای یک **Interface** چند پیاده سازی وجود داشته باشد. اگر مثلا یک سرویس جدیدی بخواهیم اضافه کنیم تنها لازم است که یک پیاده سازی جدید از **Interface** ایجاد کنیم. کامپوننت ها به هم ممکن است سرویس ارایه بدهند یعنی با هم ارتباط داشته باشند. 
 
 کامپوننت ها در داخل خودشان ممکن است نیاز  به یک object داشته باشند.  یعنی یک وابستگی وجود داشته باشد. این وابستگی باید تامین شود. IoC می گوید نرم افزار باید طوری طراجی شود که کنترل وابستگی ها از داخل کامپوننت ها هلرح شود و به یک object به نام  Container سپرده شود. در غیر این صورت این وابستگی به صورت hardcode  در داخل کامپوننت باید تامین شود که اصولی نیست چون هنگام توسعه نرم افزار باید کدها تغییر کنند. شعار IoC :

**Don`t call us , we`ll call you**

 کلاس های Pattern زیر در Spring برای IOC راهکار داده اند:
 Factory Pattern / Template Pattern / Strategy Pattern / Service Lookup
 
 دو رهیافت یا رویکرد کلی برای IOC :
 - Dependency Injection (DI)
 - Dependency Lookup (DL)
  
  این دو تا کامل کننده هم هستند . تفاوت این دو این است که در در حالت اول contatiner از بیرون می آید وابستگی را تامین می کند . در حالت دوم خود کامپوننت مسئول تامین وابستگی  خودش هست.
  
  ### Dependency Injection
  
  اشیا  (object)داخل application نباید مسدول جست و جوی منابع مورد نیاز (منابعی که با آن وابسته هستند) را داشته باشند. خود IoC container باید ایجاد object و تامین وابستگی را مدیریت کند. به دو روش می توان از Dependency Injection استفاده کرد:
  - Constructor Injection
  - Setter Injection
  ### Dependency Lookup 
 
 
