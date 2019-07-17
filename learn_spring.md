- ### 1. spring bean 的生命周期
  - 1.1 扫描 xml 文件 java 配置类中的 bean 定义
  - 1.2 创建 bean 实例
  - 1.3 注入 bean 依赖项(调用 setter,为自动装备字段设置值)
  - 1.4 如果 bean 类型实现了 BeanNameAware,则调用 setBeanName()
  - 1.5 如果 bean 实现了 ApplicationContextAware,则调用 setApplicationContext()
  - 1.6 如果存在@PostContruct 注释,则使用它注释调用方法
  - 1.7 如果 bean 类型实现了 InitializingBean,则调用 afterPropertiesSet()
  - 1.8 如果 bean 定义包含 init-method 或则@Bean(initMethod=""),则调用初始方法
  - 1.9 如果存在@preDestroy 注释,则使用它注释调用方法
  - 2.0 如果 bean 类型实现了 DisposableBean 则调用 destroy
  - 2.1 如果 bean 定义包含 destroy-method 或@Bean(destroyMethod=""),则调用销毁方法.
- ### 2. spring 事务的七种传播类型
  | 传播类型                 | 描述                                                                                |
  | ------------------------ | ----------------------------------------------------------------------------------- |
  | PROPAGATION_REQUIRED     | 支持一个已经存在的事务,如果没有事务,则开始一个新的事务                              |
  | PROPAGATION_SUPPOTS      | 支持一个已经存在的事务,如果没有事务,则以非事务方式执行                              |
  | PROPAGATION_MANDATORY    | 支持一个已经存在的事务,如果没有活动事务,则抛出异常                                  |
  | PROPAGATION_REQUIRES_NEW | 始终开始新的事务.如果活动事务已经存在,将其暂停                                      |
  | PROPAGATION_NOT_SUPPOTED | 不支持活动事务的执行.始终以非事务方式执行并暂停任何现有事务                         |
  | PROPAGATION_NEVER        | 即时存在活动事务,也始终以非事务方式执行,如果存在活动事务,则抛出异常                 |
  | PROPAGATION_NESTED       | 如果存在活动事务,则在嵌套事务中运行.如果没有活动事务,则与 PROPAGATION_REQUIRED 相同 |
