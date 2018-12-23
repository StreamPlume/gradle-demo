查看所有任务
  gradle tasks
查看 Project 的 Properties
  gradle properties



清理命令
  gradle clean

构建打包命令
  gradle clean build

编译时跳过测试，使用-x,-x参数用来排除不需要执行的任务
  gradle clean build -x test


对单个项目生效，在项目中的build.gradle修改内容

buildscript {
    repositories {
        mavenLocal()
        maven { url 'http://maven.aliyun.com/nexus/content/groups/public/' }
        maven{ url 'http://maven.aliyun.com/nexus/content/repositories/jcenter'}
        mavenCentral()
        jcenter()
        maven { url "https://repo.spring.io/snapshot" }
        maven { url "https://repo.spring.io/milestone" }
        maven { url 'http://oss.jfrog.org/artifactory/oss-snapshot-local/' }  //转换pdf使用
    }
    dependencies {
    }
}

allprojects {
    repositories {
        maven { url 'http://maven.aliyun.com/nexus/content/groups/public/' }
        maven{ url 'http://maven.aliyun.com/nexus/content/repositories/jcenter'}
    }
}


task hellWorld{
    // doLast（执行时加载）
    doLast{
        println "I'm this last."
        println "Hello World!!!"
    }

    doFirst{
        println "I'm this first."
    }
}


gradle -PconfigureDesc="this is param property" testConfigure

gradle -Dorg.gradle.project.configureDesc="this is JVM property" testConfigure