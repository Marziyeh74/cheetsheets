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
 
 کامپوننت ها در داخل خودشان ممکن است نیاز  به یک object داشته باشند.  یعنی یک وابستگی وجود داشته باشد. این وابستگی باید تامین شود. IoC می گوید نرم افزار باید طوری طراجی شود که کنترل وابستگی ها از داخل کامپوننت ها خارج شود و به یک object به نام  Container سپرده شود. در غیر این صورت این وابستگی به صورت hardcode  در داخل کامپوننت باید تامین شود که اصولی نیست چون هنگام توسعه نرم افزار باید کدها تغییر کنند.
 
 ### An example of what is the problem?!
 مثال اول:
 ```java

 # Circle.java
 Class Circle{
 
    public void draw(){
    ....
    }
 }
 
  # Triangle.java
 Class Triangle{
 
    public void draw(){
    ....
    }
 }
 #Application class 
 class Application {
 
     public static void main(String[] args){
        Triangle myTriangle = new Triangle();
        myTriangle.draw();
        
        Circle myCircle = new Circle();
        myCircle.draw();
        
     }
 }
 ```
 
طبق مثال بالا در این جا کلاس Application به کلاس هایTriangle  و Circle وابسته است. نرم افزار ما قابل توسعه نیست. اگر بخواهیم یک کلاس دیگر مانند Square ایجاد کنیم و از آن در کلاس Application استفاده کنیم باید قطعه کد هایی که برای کلاس Circle  و Triangle زدیم تکرار کنیم. یعنی تغییرات را به صورت hardcode اضافه کنیم. این روش درست نیست.

 مثال دوم :
  ```java
 
  abstract Class Shape{
 
    public abstract void draw(){
    }
 }
 
 # Circle.java
 Class Circle extends Shape{
 
    public void draw(){
    ....
    }
 }
 
  # Triangle.java
 Class Triangle extends Shape {
 
    public void draw(){
    ....
    }
 }
 #Application class 
 class Application {
 
     public static void main(String[] args){
        Shape myShape = new Triangle();
        myShape.draw();
        
        Shape myShape  = new Circle();
        myShape.draw();
        
     }
 }
 ```
در مثال دوم برای بهبود راه حل از چندریختی (polymorphyism) استفاده کردیم . به جای این که کلاس Appication با هر کلاس ارتباط داشته باشد از parent ان ها استفاده می کند. در این جا هنگام تعریف نوع شی myShape از نوع کلاس  abstract یعنی Shape می باشد. اما هنگام new کردن باید پیاده سازی مشخص شود.  و وقتی متد draw شی myShape فراخوانی می شود، در واقع متد draw کلاسی که هنگام new کردن مشخص کردیم فراخوانی می شود. بنابراین هنگام توسعه کد اگر یک Shape جدید مثلا کلاس مربع  اضافه شود، در کلاس Application هنوز به نوع کلاس در هنگام new کردن وابسته هستیم.

مثال سوم : 


  ```java
 
  abstract Class Shape{
 
    public abstract void draw(){
    }
 }
 
 # Circle.java
 Class Circle extends Shape{
 
    public void draw(){
    ....
    }
 }
 
  # Triangle.java
 Class Triangle extends Shape {
 
    public void draw(){
    ....
    }
 }
 #Application class 
 class Application {
 
     public static void main(String[] args){
        Shape myShape = new Circle();
       myDrawMethod(myShape);
        
     }
     public static void myDrawMethod(Shape shape){
        shape.draw();
    }
 }
 ```
 در مثال سوم کمی کد را بهبود داده ایم. یک متد myDrawMethod در کلاس Applicaton تعریف کردیم که فقط وابسته به کلاس abstract یعنی Shape می باشد. در main ما هر پیاده سازی از shape که خواستیم مثلا Circle را new می کنیم و شی را به متدmyDrawMethod پاس می دهیم. اما هم چنان ما در داخل main هنگام new کردن به نوع shape وابسته ایم. مشکل هنوز حل نشده .. ما خودمان مجبوریم پیاده سازی را که می خواهیم ایجاد کنیم. ما باید وابستگی کلاس Application را به نوع پیاده سازی Shape مثلا Circle یا Triangle برداریم و فقط به Shape وابسته باشد. و این وابستگی توسط یک کلاس دیگر به این کلاس تزریق شود. کاری که در مثال چهارم انجام می دهیم. 
 
 مثال چهارم : 
 
   ```java
 
 #Application class 
 class Application {
    private Shape shape;
    public setShape(Shape shape){
        this.shape=shape;
    }
   
   public void drawShape(){
        this.shape.draw();
   }
 }
 
 # in different class 
 
 class Main {
   public static void main(String[] args){
         Application app = new Application();
        Circle mycricle= new Circle();
        app.setShape(mycricle);
        app.drawShape();
 
   }
}
   
 
 ```
 در این مثال همان طور که می بینید کلاس Application فقط  به Shape وابسته است. و اگر این کلاس را به عنوان یک کامپوننت در نظر بگیریم می بینید که خودش shape را new نکرده و وابستگی به shape از بیرون از کلاس توسط کلاس دیگری که  متد setShape را فراخوانی می کند تامین می شود.
 هم چنین از چندریختگی هم استفاده شده به این صورت که در حین توسعه هر کلاس دیگری که اضافه شود فقط کافیسیت از کلاس Shape ارث بری کند. و متد drawShape را با امضای مشخص شده پیاده سازی کند. بنابراین کلاس Application تغییر نخواهد کرد.
 
 اما در بیرون از Application مثلا در یک کلاس مانند کلاس Main ما شی مورد نیازمان برای مثال  از نوع Circle ایجاد می کنیم. و آن را به متد setShape یک شی از Application پاس می دهیم. ما در این جا می توانیم شی دیگر هم new کنیم. در این زمان  پارامتر shape درمتد setShape شی app با myCricle مقداردهی می شود. سپس با فراخوانی متد drawShape شی app متد draw خصیصه shape کلاس Appication یا در واقع متد draw کلاس Circle فراخوانی می شود.
 
 اما سوال این جاست که در این مثال آخر هم بالاخره در جایی از کد خارج از application باید وابستگی به شی به صورت hard code تامین شود. یعنی ما در متد main اگر بخواهیم هر تعداد شی دیگری new کنیم باید تعداد خطوطی مشابه اضافه کنیم. این مثال ها برای این بود تا ما به کاربرد Spring برسیم. Spring دقیقا می آید همین کار را انجام می دهد یعنی عمل inject کردن را به وسیله container هایش انجام می دهد. یک سری فایل های تنظیمات دارد و وقتی برنامه اجرا می شود Spring با استفاده از  فایل تنظیمات عمل inject کردن را انجام می دهد. (در ادامه بیشتر توضیح می دهیم)و دیگر برنامه نویس لازم نیست به صورت hardCode کدی مشابه چند خط کد در متد main بنویسد.
 
  
 
شعار IoC :

**Don`t call us , we`ll call you**

 کلاس های Pattern زیر در Spring برای IOC راهکار داده اند:
 Factory Pattern / Template Pattern / Strategy Pattern / Service Lookup
 
 دو رهیافت یا رویکرد کلی برای IOC :
 - Dependency Injection (DI)
 - Dependency Lookup (DL)
  
  این دو تا کامل کننده هم هستند . تفاوت این دو این است که در در حالت اول contatiner از بیرون می آید وابستگی را تامین می کند . در حالت دوم خود کامپوننت مسئول تامین وابستگی  خودش هست.
  
  ### Dependency Injection
  
  اشیا  (object)داخل application نباید مسئولیت جست و جوی منابع مورد نیاز (منابعی که با آن وابسته هستند) را داشته باشند. خود IoC container باید ایجاد object و تامین وابستگی را مدیریت کند. به دو روش می توان از Dependency Injection استفاده کرد:
  - Constructor Injection
  - Setter Injection
  ### Dependency Lookup 
  
  خود کلاس  باید وابستگی مورد نیاز خودش را تامین کند. مثال زیر یک نمونه ای از رویکرد Dependency Lookup می با شد:
  
     ```
     
     public class Main{
      public static void main(String[] args){
      
        ApplicationContext appCtx = new ClassPathXmlApplicationContext("/config.xml");
      
        MyBean bean= appCtx.getBean("myBean");
        
      }
     
     }
     
     ```
     
  در این مثال ApplicationContext یک Container در Spring می باشد و در واقع یک interface هست. ما appCtx را با کلاسClassPathXmlApplicationContext مقداردهی می کنیم. و ادرس فایل تنظیمات را به آن می دهیم. در این فایل config.xml اشیا ما یا به اصطلاح bean های ما تعریف شده اند. ما در خط بعد شی مورد نظر خود یعنی همان mybean را از container می گیریم. در واقع با خط کد دوم شی mybean در فایل config.xml جست و جو می شود. یعنی عمل lookup انجام می شود. پس وابستگی از این طریق تامین می شود. 
 
