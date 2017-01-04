### 4.3. 定义repository接口
作为第一步，您定义一个特定的实体类Repository interface。 接口必须继承自Repository并且要定义为实体
类和一个ID类型。 如果要为该实体类实现CRUD方法，请扩展`CrudRepository`而不是`Repository`。
