<center>
     <h1>解伟凡</h1>
     <div>
         <span>
             <img src="assets/phone-solid.svg" width="18px">
             17714334692
         </span>
         ·
         <span>
             <img src="assets/envelope-solid.svg" width="18px">
             2822678135@qq.com
         </span>
     </div>
 </center>

 ## <img src="assets/info-circle-solid.svg" width="30px"> 个人信息 

 - 男，1997年出生
 - 求职意向：服务端研发工程师
 - 工作经验：3.5 年

## <img src="assets/graduation-cap-solid.svg" width="30px"> 教育经历

- 硕士，中科院计算所，计算机应用技术专业，2019.9~2022.6
- 学士，东南大学，信息工程专业，2015.9~2019.6

## <img src="assets/briefcase-solid.svg" width="30px"> 工作经历

**eBay上海，风控部门，软件工程师，2022.7~2025.3**

开发维护相关的基础设施软件以及业务逻辑，主要参与/负责以下工作:
- 风控模型配置管理平台Model Inference Bridge，提高算法团队模型集成到业务的效率
- 低延迟/多维度的风控明细检索平台Risk Insight Tool，提高分析团队案例调查的效率
- 200+ 实时/离线特征的开发上线，支持策略团队的规则迭代及算法团队的模型迭代


## <img src="assets/project-diagram-solid.svg" width="30px"> 项目经历

**Model Inference Bridge(将模型快速集成到业务的配置管理平台)**

  - 项目背景
   

   风控业务的 40+ Checkpoint 划分在 5+ 业务服务中，对于模型推理，
   最初设计是业务服务直连模型服务，特征获取及推理调用的逻辑硬编码在业务服务中，
   单个Checkpoint最多可涉及1000+特征获取以及20+模型，频繁的 <strong>模型 > 特征 </strong> 迭代依赖高频率
   业务服务发版，通常以<strong>天/周</strong>为单位才能完成模型集成，影响投产效率

   Model Inference Bridge将频繁修改的推理前逻辑与业务服务解耦，桥接业务服务和模型服务，将模型集成的时间压缩至
   <strong>小时</strong> 级别。同时在内部使用缓存以及多线程优化，基本抵消额外的服务调用延迟



  - 主要工作

  1. 将特征获取及推理调用单独划分为Model Inference Bridge服务，基于 <strong> MongoDB </strong> 设计 <strong>业务 > 模型 > 特征</strong> 三个层次的多文档元数据治理
  
  2. 搭建 <strong> 内存 > Redis > MongoDB </strong> 多层缓存，处理 <strong> 日均3000万 </strong> 推理请求

  3. 使用线程池优化特征提取，将变量获取的P999延迟限制在500毫秒内

  4. 针对读多写少的实际请况，通过MongoDB事务保证多文档元数据的一致性
  

**Risk Insight Tool(用于风控调查分析的搜索平台)**


  - 项目背景

  风控分析团队在进行案例调查时多以业务离线数仓为数据源，这带来2个问题：
 
  1. 单一案例可能涉及复杂的多表查询，调试运行至少以分钟为单位，通常要调查一批用户，相对耗时且重复性工作较多
  
  2. 离线数仓多带有 <strong> T + 1 </strong>延迟，如果要实时调查还需要研发Oncall介入查询日志，沟通成本更大

  Risk Insight Tool 通过 ETL 将案例调查常用的 <strong> DW表 -- Kafka流 </strong>数据进行预计算并写入Elasticsearch，将繁琐的<strong> 数仓 -- 日志 </strong>查询
  变为Kibana检索和 RESTFul API调用，使得分析团队可以及时自助地捞取365d数据且P99延迟维持在1秒内


  - 主要工作

  1. 基于 <strong> Kafka > Flink > ElasticSearch </strong> 搭建实时管道，存储热字段

  2. 基于Spark搭建离线管道，用于历史数据恢复

  3. 变更频繁或存储开销大的字段通过集成相关服务做运行时提取

  4. 使用CompletableFuture优化跨服务取数链路，将查询的P99延迟维持在1秒内


## <img src="assets/tools-solid.svg" width="30px"> 技能清单

- 编程语言：熟练掌握Java及Spring技术栈，了解python和c++
- 关系型数据库： 熟悉MySQL
- 搜索引擎：熟悉ElasticSearch
- 消息队列：熟悉Kafka
- NoSQL数据库：熟悉Redis，了解MongoDB
- 大数据相关：了解Flink，Spark，Hive
