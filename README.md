# 支付平台


![](./images/支付平台架构.png)



支付系统从架构上来说，分为三层;

**支撑层**： 用来支持核心系统的基础软件包和基础设施， 包括运维监控系统、日志分析系统等。

**核心层**： 支付系统的核心模块，内部又分为两个部分： 支付核心模块以及支付服务模块。

**产品层**： 通过核心层提供的服务组合起来，对最终用户、商户、运营管理人员提供的系统。

---------------------

### 支撑系统

支撑系统是一个公司提供给支付系统运行的基础设施。 主要包括如下子系统：

`运维监控`： 支付系统在下运行过程中不可避免的会受到各种内部和外部的干扰，光纤被挖断、黑客攻击、数据库被误删、上线系统中有bug等等，运维人员必须在第一时间内对这些意外事件作出响应，又不能够一天24小时盯着。这就需要一个运维监控系统来协助完成。

`日志分析`： 日志是支付系统统计分析、运维监控的重要依据。公司需要提供基础设施来支持日志统一收集和分析。

`短信平台`： 短信在支付系统中有重要作用： 身份验证、安全登录、找回密码、以及报警监控，都需要短信的支持。

`安全机制`： 安全是支付的生命线。 SSL、证书系统、防刷接口等，都是支付的必要设施。

`统计报表`： 支付数据的可视化展示，是公司进行决策的基础。

`远程连接管理`、分布式计算、消息机制、全文检索、文件传输、数据存储、机器学习等，都是构建大型系统所必须的基础软件，这里不再一一详细介绍。

### 支付核心系统

支付核心系统指用户执行支付的核心流程，包括：

用户从支付应用启动支付流程。

支付应用根据应用和用户选择的支付工具来调用对应的支付产品来执行支付。

支付路由根据支付工具、渠道费率、接口稳定性等因素选择合适的支付渠道来落地支付。

支付渠道调用银行、第三方支付等渠道提供的接口来执行支付操作，最终落地资金转移。

### 支付服务系统

支持支付核心系统所提供的功能。服务系统又分为基础服务系统、资金系统、风控和信用系统。

基础服务系统提供支撑线上支付系统运行的基础业务功能：

`客户信息管理`：包括对用户、商户的实名身份、基本信息、协议的管理；

`卡券管理`： 对优惠券、代金券、折扣券的制作、发放、使用流程的管理；

`支付通道管理`: 通道接口、配置参数、费用、限额以及QOS的管理；

`账户和账务系统`： 管理账户信息以及交易流水、记账凭证等。这里的账务一般指对接线上系统的账务，采用单边账的记账方式。 内部账记录在会计核算系统中。

`订单系统`： 一般订单系统可以独立于业务系统来实现的。这里的订单，主要指支付订单。

资金系统指围绕财务会计而产生的后台资金核实、调度和管理的系统，包括：

`会计核算`： 提供会计科目、内部账务、试算平衡、日切、流水登记、核算和归档的功能。

`资金管理`： 管理公司在各个支付渠道的头寸，在余额不足时进行打款。 对第三方支付公司，还需要对备付金进行管理。

`清算分润`： 对于有分润需求的业务，还需要提供清分清算、对账处理和计费分润功能。

风控系统是支付系统必备的基础功能，所有的支付行为必须做风险评估并采取对应的措施；信用系统是在风控基础上发展的高级功能，京东的白条，蚂蚁花呗等，都是成功的案例。

### 支付应用

支撑系统、核心系统和服务系统，在每个公司的架构上应该是大同小异的，都是必不可少的模块。而支付应用是每个公司根据自己的业务来构建的，各不相同。 总的来说，可以按照使用对象分为针对最终用户的应用、针对商户的应用、针对运营人员的运营管理、BI和风控后台。
