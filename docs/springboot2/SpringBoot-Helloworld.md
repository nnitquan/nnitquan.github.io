# 

## 前置条件

## 生成Maven代码框架

    mvn archetype:generate -DgroupId=org.nnitquan.helloworld -DartifactId=helloworld -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

敲入命令后返回输出：

    zergl@HODOR MINGW64 /c/workspace/code/javacode/spring_boot_code
    =falsearchetype:generate -DgroupId=org.nnitquan.helloworld -DartifactId=helloworld -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode
    [INFO] Scanning for projects...
    [INFO]
    [INFO] ------------------------------------------------------------------------
    [INFO] Building Maven Stub Project (No POM) 1
    [INFO] ------------------------------------------------------------------------
    [INFO]
    [INFO] >>> maven-archetype-plugin:3.0.1:generate (default-cli) > generate-sources @ standalone-pom >>>
    [INFO]
    [INFO] <<< maven-archetype-plugin:3.0.1:generate (default-cli) < generate-sources @ standalone-pom <<<
    [INFO]
    [INFO]
    [INFO] --- maven-archetype-plugin:3.0.1:generate (default-cli) @ standalone-pom ---
    [INFO] Generating project in Batch mode
    [INFO] ----------------------------------------------------------------------------
    [INFO] Using following parameters for creating project from Old (1.x) Archetype: maven-archetype-quickstart:1.0
    [INFO] ----------------------------------------------------------------------------
    [INFO] Parameter: basedir, Value: C:\workspace\code\javacode\spring_boot_code
    [INFO] Parameter: package, Value: org.nnitquan.helloworld
    [INFO] Parameter: groupId, Value: org.nnitquan.helloworld
    [INFO] Parameter: artifactId, Value: helloworld
    [INFO] Parameter: packageName, Value: org.nnitquan.helloworld
    [INFO] Parameter: version, Value: 1.0-SNAPSHOT
    [INFO] project created from Old (1.x) Archetype in dir: C:\workspace\code\javacode\spring_boot_code\helloworld
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD SUCCESS
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 38.167 s
    [INFO] Finished at: 2018-04-02T02:44:00+08:00
    [INFO] Final Memory: 16M/53M
    [INFO] ------------------------------------------------------------------------

目录层级：

    $ tree helloworld
    helloworld
    |-- pom.xml
    `-- src
        |-- main
        |   `-- java
        |       `-- org
        |           `-- nnitquan
        |               `-- helloworld
        |                   `-- App.java
        `-- test
            `-- java
                `-- org
                    `-- nnitquan
                        `-- helloworld
                            `-- AppTest.java
    
    11 directories, 3 files


## 3.集成SpringBoot框架

### 3.1 修改入口类源代码
    index e68b750..6363518 100644
    --- a/src/main/java/org/nnitquan/helloworld/App.java
    +++ b/src/main/java/org/nnitquan/helloworld/App.java
    @@ -1,13 +1,18 @@
     package org.nnitquan.helloworld;
    
    +import org.springframework.boot.SpringApplication;
    +import org.springframework.boot.autoconfigure.SpringBootApplication;
    +
     /**
      * Hello world!
      *
      */
    +@SpringBootApplication
     public class App
     {
         public static void main( String[] args )
         {
    -        System.out.println( "Hello World!" );
    +        //System.out.println( "Hello World!" );
    +        SpringApplication.run(App.class);
         }
     }

### 3.2 新增一个Controller类

src/main/java/org/nnitquan/helloworld/HelloworldController.java

      1 package org.nnitquan.helloworld;
      2
      3 import org.springframework.web.bind.annotation.RequestMapping;
      4 import org.springframework.web.bind.annotation.RestController;
      5
      6 @RestController
      7 public class HelloworldController {
      8     @RequestMapping("/helloworld")
      9     public String sayHello() {
     10         return "Hello, SpringBoot! @nnitquan";
     11     }
     12 }


### 3.3 修改pom.xml并编译

    diff --git a/pom.xml b/pom.xml
    index b1c1e52..8ea9571 100644
    --- a/pom.xml
    +++ b/pom.xml
    @@ -7,7 +7,30 @@
       <version>1.0-SNAPSHOT</version>
       <name>helloworld</name>
       <url>http://maven.apache.org</url>
    +
    +  <parent>
    +       <groupId>org.springframework.boot</groupId>
    +       <artifactId>spring-boot-starter-parent</artifactId>
    +       <version>2.0.0.RELEASE</version>
    +  </parent>
    +
       <dependencies>
    +       <dependency>
    +               <groupId>org.springframework.boot</groupId>
    +               <artifactId>spring-boot-starter-web</artifactId>
    +       </dependency>
    +
    +       <dependency>
    +               <groupId>org.springframework.boot</groupId>
    +               <artifactId>spring-boot-starter-test</artifactId>
    +               <scope>test</scope>
    +       </dependency>
    +
    +       <dependency>
    +               <groupId>com.jayway.jsonpath</groupId>
    +               <artifactId>json-path</artifactId>
    +               <scope>test</scope>
    +       </dependency>
         <dependency>
           <groupId>junit</groupId>
           <artifactId>junit</artifactId>
    @@ -22,4 +45,12 @@
            <maven.compiler.target>1.9</maven.compiler.target>
       </properties>
    
    +  <build>
    +       <plugins>
    +               <plugin>
    +                       <groupId>org.springframework.boot</groupId>
    +                       <artifactId>spring-boot-maven-plugin</artifactId>
    +               </plugin>
    +       </plugins>
    +  </build>
     </project>

执行命令编译：

    $ mvn package

### 3.4 运行并测试

    $ java -jar target/helloworld-1.0-SNAPSHOT.jar
    
### 3.5 浏览器访问并验证
运行jar后，浏览器访问：http://127.0.0.1:8080/helloworld

### 3.6 其他
(1) RequestMapping的几种方式

(2)

## 问题集合

### 1.编译时JDK版本不匹配

    $ mvn compile
    [INFO] Scanning for projects...
    [INFO]
    [INFO] ------------------------------------------------------------------------
    [INFO] Building helloworld 1.0-SNAPSHOT
    [INFO] ------------------------------------------------------------------------
    [INFO]
    [INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ helloworld ---
    [WARNING] Using platform encoding (GBK actually) to copy filtered resources, i.e. build is platform dependent!
    [INFO] skip non existing resourceDirectory C:\workspace\github\nnitquan.github.io\docs\springboot2\helloworld\src\main\resources
    [INFO]
    [INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ helloworld ---
    [INFO] Changes detected - recompiling the module!
    [WARNING] File encoding has not been set, using platform encoding GBK, i.e. build is platform dependent!
    [INFO] Compiling 1 source file to C:\workspace\github\nnitquan.github.io\docs\springboot2\helloworld\target\classes
    [INFO] -------------------------------------------------------------
    [ERROR] COMPILATION ERROR :
    [INFO] -------------------------------------------------------------
    [ERROR] 不再支持源选项 1.5。请使用 1.6 或更高版本。
    [ERROR] 不再支持目标选项 1.5。请使用 1.6 或更高版本。
    [INFO] 2 errors
    [INFO] -------------------------------------------------------------
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD FAILURE
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 1.488 s
    [INFO] Finished at: 2018-05-07T11:17:54+08:00
    [INFO] Final Memory: 10M/34M
    [INFO] ------------------------------------------------------------------------
    [ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.1:compile (default-compile) on project helloworld: Compilation failure: Compilation failure:
    [ERROR] 不再支持源选项 1.5。请使用 1.6 或更高版本。
    [ERROR] 不再支持目标选项 1.5。请使用 1.6 或更高版本。
    [ERROR] -> [Help 1]
    [ERROR]
    [ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
    [ERROR] Re-run Maven using the -X switch to enable full debug logging.
    [ERROR]
    [ERROR] For more information about the errors and possible solutions, please read the following articles:
    [ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoFailureException
    
解决方式：在pom.xml添加maven编译关联的版本号（本机安装了java 9 sdk）

    </project>
      ......
      <properties>
        <java.version>1.9</java.version>
        <maven.compiler.source>1.9</maven.compiler.source>
        <maven.compiler.target>1.9</maven.compiler.target>
      </properties>
    
    </project>

