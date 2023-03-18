项目总结报告

这是一个典型的前后端分离的Web应用程序。其中，Vue用于前端UI的开发，Spring Boot用于后端服务的提供，Mybatis-plus用于数据持久层的访问。

技术难点：

1.跨域问题

​			由于前端和后端代码分别部署在Web服务器和应用服务器上，因此会遇到跨域问题。

2.实体类映射

​			在后端代码中，需要将数据库中的实体类映射到Java类中。

3.接口设计和调试

​			在前后端分离的应用程序中，接口是前后端通信的关键。在设计接口时，需要考虑到参数传递、请求方式、数据格式和数据校验等因素。

解决方案：

1. 跨域问题可以通过在后端代码中添加跨域访问的支持，或者通过使用代理服务器等方式来解决这个问题。

2. Mybatis-plus提供了ORM（对象关系映射）功能，可以帮助开发人员快速以Java对象的形式访问数据库中的数据。

3. 在设计接口时，可以借助在线工具和开发工具Postman来帮助设计和调试接口。同时，采用Restful API规范，统一接口的数据交互格式和请求方式，提高接口的可维护性和扩展性。

   

   后续项目复盘建议：

   1. 前端性能优化

      通过减少DOM操作、压缩和缓存静态资源、按需加载JavaScript、通过懒加载减少初始页面加载时间等方式来优化前端性能。

   2. 后端性能优化

      后端可通过缓存访问数据库和其他服务的结果、限制资源使用、使用线程池和异步处理等方式来提高性能。还可以考虑在后端服务器上实现数据压缩、HTTP缓存和负载均衡等功能。

   3. 安全性检查

      要检查是否存在潜在的安全漏洞，如注入攻击、跨站脚本攻击、会话劫持攻击等。在后端代码中可以使用有效的验证技术和防护机制，如参数验证、XSS安全性过滤、CSRF令牌、安全Socket层（SSL）和管理认证等。

   4. 日志和监控

      在开发和生产环境中，都应该加强日志记录和监测功能，以便及时发现和解决任何问题。可以使用监控和日志记录工具，如Prometheus和ELK（Elasticsearch、Logstash和Kibana），来收集和呈现应用程序的运行时信息和性能指标。

   5. 代码优化和规范

      代码质量对应用程序的功能、可维护性和可扩展性都有重要的影响。可以使用静态代码分析工具、代码评审和测试技术等进行代码优化，并采用良好的编程规范和标准，使代码更加规范化并易于理解和维护。

      

      时间少，匆匆忙忙写的这个项目，只有最基础的增删查改登录注册功能，后续有时间将对整个项目进行复盘，完善功能

      需要了解更多开发资讯，欢迎关注公众号Eersan