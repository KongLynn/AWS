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
## AWS WAF
1. 一个web ACL可关联多个aws资源，一个aws资源只能关联一个web ACL
2. waf本质就是web ACL
3. web ACL与cdn关联后，不能与其他aws资源关联
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

## rds
1. 
## cloud watch
1. 基于指标，若基于事件/操作使用event bridge
## hpc
1. hpc集群应在单个AZ中；
2. 
## cloudformation
1. 创建模版时需要给ec2授与访问db的IAM角色，应在实例的配置文件属性中引用该角色
## direct connect
1. 仅使用 Direct Connect 连接到 EC2 等服务，您需要创建一个私有 VIF。 但是，如果您想加密流经 DirectConnect 的流量，您将需要使用 DX 的公共 VIF 来创建允许访问 AWS 服务（如 S3、EC2 等）的 VPN 连接。https://aws.amazon.com/premiumsupport/knowledge-center/create-vpn-direct-connect/.
2. 
## system manager

1. 可以使用RDP管理ec2而不需要ssh
2. 

## step function
1. 使用json作为输入输出
2. 
## AWS SSO
1. AWS SSO不支持移动应用程序
2. 

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
2.
