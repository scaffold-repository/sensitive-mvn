# 说明
maven中依赖

    <repositories>
        <repository>
            <id>github</id>
            <url>https://raw.github.com/scaffold-repository/sensitive-mvn/master/</url>
            <snapshots>
                <enabled>true</enabled>
                <updatePolicy>always</updatePolicy>
            </snapshots>
        </repository>
    </repositories>
    
    <dependency>
        <groupId>com.scaffold</groupId>
        <artifactId>sensitive-filter-starter</artifactId>
        <version>1.0</version>
    </dependency>
        
        
# 用法
 
- 2.配置敏感词文件

```xml
在您的application.properties文件中添加
com.scaffold.sensitive.sensitive-file=zh.txt,bl.txt,wz.txt,sq.txt
zh为政治，bl为暴力，sq是色情，wz网站
```

- 3.开启注解
在启动类上开启注解：`@EnableSensitive`

```java
@EnableSensitive
@SpringBootApplication
public class tet implements ApplicationContextAware {

    public static void main(String[] args) {
        SpringApplication.run(tet.class, args);
    }
}
```


 - 4.注入敏感词检测实体
 
```xml
   @Autowird
   private WordFilter wordFilter;
```

- 5.敏感词检测的接口

```xml
    Stirng test="123123123"
    if (wordFilter.isContains(test)){
        System.out.println("yes contain");
    }else{
        System.out.println("ok contain");
    }
