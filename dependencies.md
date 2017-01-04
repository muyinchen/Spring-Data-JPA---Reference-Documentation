## 3. Dependencies

由于各个Spring Data模块的初始日期不同，大多数模块带有不同的主版本号和次版本号。 找到兼容版本的最简单的方法是依靠Spring Data Release Train BOM，我们提供兼容的版本定义。 在Maven项目中，你可以在POM的`<dependencyManagement/>`部分声明这个依赖关系：

示例1.使用Spring Data发行版BOM

```xml
<dependencyManagement>
  <dependencies>
    <dependency>
      <groupId>org.springframework.data</groupId>
      <artifactId>spring-data-releasetrain</artifactId>
      <version>${release-train}</version>
      <scope>import</scope>
      <type>pom</type>
    </dependency>
  </dependencies>
</dependencyManagement>
```