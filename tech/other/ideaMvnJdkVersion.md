## mvn 设置默认编译jdk

 + 最近公司一个项目，pom.xml没有指定默认编译的jdk版本，导致Idea在每次分支切换的时候，都会执行Reimport，然后mvn的默认Jdk被设置为1.5，然后jdk1.5是不支持@Override注解的，然后文件全是错误。
 
 
 
### 一劳永逸的方法

+ 保证所有子模块的pom都继承主pom.类似下面这样的


```
<parent>
		<groupId>com.haha.hehe</groupId>
		<artifactId>test</artifactId>
		<version>1.0-SNAPSHOT</version>
</parent>
```

+ 然后在主pom中找到maven-compiler-plugin插件，如果没有，那么就按照下面配置

```
<build>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.1</version>
				<configuration>
					<encoding>${java.encoding}</encoding>
                    <source>${java.version}</source>
                    <target>${java.version}</target>
				</configuration>
			</plugin>
		</plugins>
</build>

```

+ 如果能找到，那么就在<configuration></configuration>键值对内加上<source>和<target>的配置。


### over

 
 

