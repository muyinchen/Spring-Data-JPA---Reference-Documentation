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
