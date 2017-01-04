#### 4.3.1. 调整repository定义

通常，您的repository接口将扩展`Repository`，`CrudRepository`或`PagingAndSortingRepository`。 或者，如果不想扩展Spring Data接口，也可以使用`@RepositoryDefinition`注解声明你的Repository interface。 扩展`CrudRepository`提供了一套完整的方法来操做你的实体。 如果你喜欢选择性的暴露某些方法，只需将你想要暴露的方法从“CrudRepository”复制到你的domain repository中。

| **   | 这允许您在提供的Spring Data Repositories功能之上定义自己的抽象. |
| ---- | ---------------------------------------- |
|      |                                          |

Example 7. 选择性暴露CRUD方法

```java
@NoRepositoryBean
interface MyBaseRepository<T, ID extends Serializable> extends Repository<T, ID> {

  T findOne(ID id);

  T save(T entity);
}

interface UserRepository extends MyBaseRepository<User, Long> {
  User findByEmailAddress(EmailAddress emailAddress);
}
```
在这个第一步，你为所有的实体类repositories定义了一个公共基础接口并暴露了`findOne（...）`和`save（...）`方法。这些方法将通过Spring Data路由到您选择的存储库的基础仓库实现，例如JPA`SimpleJpaRepository`，因为他们在`CrudRepository匹配到这些方法签名`。 所以'UserRepository`现在可以保存用户，并通过id找到单个，同样的也可以通过他们的邮件地址查
询找到这些用户。

| **   | 注意，中间repository接口注释为`@ NoRepositoryBean`。 确保将该注解添加到所有repository interfaces，Spring Data不应在运行时创建实例. |
| ---- | ---------------------------------------- |
|      |                                          |