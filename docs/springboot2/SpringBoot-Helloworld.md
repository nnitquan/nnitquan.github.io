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
