# Context

MyBatis Generator 定制插件库（`mbg-plugin-pky`），为下游业务工程提供统一的代码生成增强约定。

## Core Terms

**Custom Plugin (定制生成插件)**:
在 MyBatis Generator 生成实体与 Mapper 阶段注入项目统一约定的扩展点，负责补充数据库列注释 Javadoc、Lombok 注解、公共基类/基接口（`BasicEntity` / `BasicMapper`）、通用更新辅助方法（`updateAllColumns`、`updateSelectiveColumns`、`getSqlTable`）并移除 `@Generated` 注解。
_Avoid_: 在插件中直接耦合特定业务表名, 依赖 MyBatis Generator 内部已移除的私有日志工厂（如 `LogFactory`）, 为 `mybatis-dynamic-sql` 2.0 的非泛型 `UpdateDSL` 添加 `<UpdateModel>` 泛型参数

**Bundled Distribution (内置 Jar 分发包)**:
下游工程通过本地 `lib/mbg-plugin-pky.jar` 引用的离线构建产物，插件源码升级或兼容新版本 JDK / MyBatis Generator 后须重新打包并同步替换该 Jar。
_Avoid_: 只改插件源码不同步下游 Jar 产物
