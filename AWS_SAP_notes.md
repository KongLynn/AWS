## VPC


## VPC Peering
1. 使用VPC Peering CIDR地址块不能重叠
2. 接受者VPC可以属于另一个AWS帐户，并且可以位于请求者VPC的不同地区。
3. 跨账户建立VPC Peering需要在接受者账户创建跨账户访问角色
4.        

## Route53
1. 故障转移路由策略 - 当您要配置主动-被动故障转移时使用。
延迟路由策略 – 当您在多个 AWS 区域中拥有资源并且您希望将流量路由到提供最佳延迟的区域时使用
简单路由策略 - 对于为您的域执行给定功能的单一资源（例如为 example.com 网站提供内容的 Web 服务器），可以使用该策略。在私有托管区域中，可以使用简单的路由创建记录。
故障转移路由策略 - 如果您想要配置主动-被动故障转移，则可以使用该策略。在私有托管区域中，可以使用失效转移路由创建记录。
地理位置路由策略 - 如果您想要根据用户的位置来路由流量，则可以使用该策略。在私有托管区域中，可以使用地理位置路由创建记录。
地理位置临近度路由策略 - 用于根据资源的位置来路由流量，以及（可选）将流量从一个位置中的资源转移到另一个位置中的资源。
延迟路由策略 – 如果您的资源位于多个 AWS 区域，并且您想要将流量路由到提供最佳延迟的区域，则可以使用该策略。在私有托管区域中，可以使用延迟路由创建记录。
基于 IP 的路由策略 – 如果您希望根据用户的位置来路由流量，并且获得流量来源的 IP 地址，则可以使用该策略。
多值应答路由策略 - 如果您想要让 Route 53 用随机选择的正常记录（最多八条）响应 DNS 查询，则可以使用该策略。在私有托管区域中，可以使用多值应答路由创建记录。
加权路由策略 - 用于按照您指定的比例将流量路由到多个资源。在私有托管区域中，可以使用加权路由创建记录。

## Transit gateway
1. 使用transit gateway在每个成员账户的vpc之间建立连接：使用AWS resource manager与成员账户共享transit gateway，在主账户启动cloud formation stack set，自动在成员账户创建vpc和attachment，将attachment与transit gateway ID关联
## scp
1. scp只影响成员账户，不影响主账户
2. 
## ec2
1. EC2不提供内存相应的指标，####如果您想收集并查看内存指标，您可以通过自定义指标，然后从EC2上推送到CloudWatch进行查看。

## spot实例
1. draining实例耗尽，收到实例终止通知两分钟内中断ecs任务，并在集群其他位置调度替换任务

## S3
1. data access patterns are unpredictable最适合智能分层
2. IAM Policy是global级别的，他是针对用户来设置的，比如一个用户对所有的S3Bucket拥有get和list权限，那他就可以浏览任何一个Bucket的内容； 相较而言，S3 Bucket Policy仅仅是针对单个Bucket 而言的，他可以控制不同用户对他本身的访问权限；Bucket ACL是一个早期的服务，现在用的比较少了，但是如果我们需要对Bucket其中的具体对象配置访问权限，我们需要使用Bucket ACL。
3. 创建跨区域副本：目标区域创建S3——两个S3之间设置跨区域复制——创建角色允许从源S3复制到目的S3，将角色分配给S3
4. 

## EFS
1. 给另一个AWS账户授予从EC2访问自己的EFS：识别IP地址，在EC2的/etc/hosts添加该IP地址
## S3 Access Point
1. Amazon S3接入点是S3的一项功能，简化了将数据存储在S3中的任何AWS服务或客户应用程序的数据访问。使用S3接入点，客户可以为每个接入点创建独特的访问控制策略，以轻松控制对共享数据集的访问。App --S3 Access Point --S3 Gateway Endpoint --S3 Bucket

## AWS WAF
1. 一个web ACL可关联多个aws资源，一个aws资源只能关联一个web ACL
2. waf本质就是web ACL
3. web ACL与cdn关联后，不能与其他aws资源关联
4. aws waf可以设置拦截特定国家/地区的请求
## tag editor
1. 使用tag editor修复未标记的资源是最佳实践
## auto scaling
1. 跨可用区，不能跨区域

## dynamodb
1. nosql数据库但可以处理结构化数据
2. autoscaling要在峰值持续几分钟后才会响应
3. 百万级别的访问高峰，在这时间段给dynamodb扩展读取和写入成本很高，可以使用sqs卸载，降低在dydb的读取和写入成本
4. 可进行精细（行级）访问控制
5. dynamodb不支持跨区域强一致性读取
6. 全局表是一个或多个副本的集合

## RDS
1. RDS代理可解决高连接的问题
2. 
## cloud watch
1. 基于指标，若基于事件/操作使用event bridge
## hpc
1. hpc集群应在单个AZ中；
2. 
## cloudformation
1. 创建模版时需要给ec2授与访问db的IAM角色，应在实例的配置文件属性中引用该角色
## direct connect
1. 仅使用 Direct Connect 连接到 EC2 等服务，您需要创建一个私有 VIF。 但是，如果您想加密流经 DirectConnect 的流量，您将需要使用 DX 的公共 VIF 来创建允许访问 AWS 服务（如 S3、EC2 等）的 VPN 连接。https://aws.amazon.com/premiumsupport/knowledge-center/create-vpn-direct-connect/.

## system manager

1. 可以使用RDP管理ec2而不需要ssh
2. 会话管理器可以在会话期间进行活动日志记录 + 提供转发端口的能力.

## step function
1. 使用json作为输入输出
2. 
## AWS SSO
1. AWS SSO不支持移动应用程序


## EFS
1. 没有跨区域复制功能

## secret manager
1. parameter store不提供自动轮换，parameter store允许将存储密钥，然后将密钥作为参数引用
2. 

## Appsync
1. 无服务器grahql和pub/sub api服务，简化web和app的构建
2. 

## cloudendure migration
1. 快速迁移windows和linux的应用程序和数据库
2. 

## SCT schema conversion tool
1. 用于转换数据库架构
2. 

1. 将只读副本提升为主副本并使用cloudformation恢复ami比快照恢复快
2. 
## Amazon pinpoint
1. 多渠道营销传播服务，如邮件、消息推送


## AWS Trust Advisor
1. AWSTrust Advisor提供建议，帮助您遵循AWS最佳实践。受信任的 Advisor（技术顾问）通过检查来评估您的帐户。这些检查确定了优化AWS基础设施、提高安全性和性能、降低成本和监控服务配额的方法。

## Athena
1. 控制Athena成本使用Athena workgroups设置扫描数据量的限制；
2. 
## secret manager

## Amazon DLM（Data Lifecicle Manager）
1. 配置策略将EBS快照复制到其他区域
2. 
## secret manager
