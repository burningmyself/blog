# 微服务架构的设计原则

## 微服务架构的设计原则如下：
1. 高内聚、低耦合。
2. 无缝的 API 集成。
3. 为每一项服务分配唯一的资源标识。
4. 实时流量管理。
5. 最小化数据表，以优化加载。
6. 通过内/外部 API，执行持续监控。
7. 为每个微服务隔离数据的存储。这对于限制数据的访问和避免“服务的耦合”是非常有用的。
例如：基于用户的分类数据，我们可以实施命令查询的责任分离（Command Query Responsibility Segregation，CQRS）。
8. 去中心化。设计微服务架构的首要原则是：将单体结构分解成独立的多个实体，而这些实体就被称为微服务。
这些微服务能够独立于其他的系统功能提供服务，用户对它们采取的所有编辑、删除、或在其他地方的使用，都不会影响到本系统的整体性能。
9. 可扩展性。微服务的设计目标是：性能与效率。在现实世界中，解决大型系统的可扩展性问题，是任何微服务生态系统的性能体现。
虽然丰富的技术功能给大量的数据工作带来了多种数据片段，但是如果能恰当地实施、并使用各种应用程序控制器（Application Controllers），则会让微服务架构更具可扩展性。
10. 通过与 DevOps 的集成，实现持续交付。DevOps 的多技术互通与融合，比较适合于微服务架构。在设计微服务架构时，我们需要关注性能和系统效率的提升，这正好契合了 DevOps 的更快交付出方案的理念。
相对于传统的单体式设计，它更适合于部署性、可靠的和可扩展性的方案管理。

当然，相对于上述各项原则与优势，微服务架构也有着一定的局限性。不过好在我们拥有多种微服务的设计模式可供选择，来实现自己的系统设计目标。下面让我们来逐一进行讨论。

## 针对有效协作的微服务设计模式

高效的微服务架构必须能够让多个微服务实现有效的协作和同步运行。

### 聚合器微服务设计模式
由于会涉及到多种业务，我们有必要为最终用户截获输出、并将其予以合并。

对于用户来说，如果他们想自行合并数据，则需要具有对于系统的大量内部知识。

那么，我们在设计微服务架构时，为了打破这种单体性，就应当根据输出来进行资源的划分。因此，我们利用聚合器模式，来汇总这些数据。

这种方案可以通过两个主要组件，来呈现给最终用户。其中的一种是带有 API 网关的复合式微服务。它可以汇总数据，并将其转发给用户。

如果您需要在分解的系统中用到各种业务功能模块的话，复合式微服务应当成为您的首选。

### 分支微服务设计模式

此模式扩展了聚合器的设计模式。在分支模式下，您可以通过两个独立的（更精确地说是：互斥的）微服务链，来同时处理请求和响应。

这种设计模式能够根据您的不同业务需求，为单个或多个服务链提供灵活性。

例如：针对某个电子商务网站或 Web 应用程序，我们可能按需接收来自不同微服务的多个数据源。

### 后端为前端/API 网关

从每个运行服务处获取数据，是任何应用程序的首要任务。对于微服务架构而言，从独立的服务中提取数据，同样非常重要。

但是，仅通过一个用户界面（UI），从大量的微服务中获取用户手中的资源信息，并不是一件容易的事。

因此，就像企业里的服务台那样，我们可以在微服务架构中，用 API 网关来为所有的交互操作提供统一的入口。

另外，在安全方面，API 网关也有助于实现用户的授权、和为合适的用户提供相关的 API。

因此 API 网关作为单一的切入点，不仅能够充当代理服务器的作用，将各种请求路由到不同的微服务那里，还能汇总来自多个服务的输出结果，并发送给用户。

它可以处理多种协议请求，并按需进行转换（例如，实现 HTTPS 与 AMQP 之间的互转）。

## 针对性能监控的微服务设计模式

性能监测是确保微服务架构成功的另一个重要方面。它有助于衡量系统的效率，并获悉拖慢系统的罪魁祸首。下列模式涉及到可观测性的范畴，能够保障微服务架构设计的鲁棒性。

### 日志聚合

微服务是可以独立地、并行地支持多种其他服务的。而且，它的实例能够横跨各台机器。

同时，每个服务都会根据其执行情况生成一个日志入口。那么我们该如何跟踪这些大量的服务相关日志呢？

这正是日志聚合模式的切入点。为了防止出现混乱的局面，我们应当设置一个可以对所有微服务实例进行日志聚合的主服务。而且，这种集中式日志应当具有搜索和监控的功能。

### 综合监控（或称语义监控）

对微服务架构的监控，是一项繁琐、但又必要的任务。当有数百个服务同时运行时，要想在日志库里查明某个失败的根本原因，那就更难了。此时，综合监控可能会派上用场。

在您进行自动化测试时，综合监控能够帮助您将结果与生产环境定期进行映射和比较。一旦出现故障，用户将及时得到相关警告。

另外，语义监控还能帮助您实现如下两方面：
1. 监测自动化的测试案例。
2. 根据业务需求，检测生产环境中的故障。

同时，随着系统的负载和微服务数量的增加，对系统性能的持续监控，并跨服务发现潜在的问题，就显得非常重要了。

我们可以通过指标服务（metric service）来收集各类数据。指标服务可以是“推式”和“拉式”两种形式。

顾名思义，推式服务（如：AppDynamics）是将捕捉到的数据指标推送到服务端；而拉式服务（如：Prometheus）则负责从服务中拉取对应的数据指标。

## API 健康检查

微服务架构的设计促进了各个服务之间的相互独立，并避免了系统中的任何延迟。

我们知道，API 在网络连接中能够起到基石作用。我们需要通过对 API 的定期健康检查，来提前发现各种障碍。

例如，您可能会经常观察到：某个微服务虽然处于启动和和运行状态，却没有能力去处理任何请求。

那么，以下便是一些导致 API 故障的因素：
* 服务器的负载
* 用户的使用量
* 各种延迟
* 错误日志
* 下载量

为了应对上述因素，我们应该确保每一个服务在运行时，都配有一个健康检查的特定 API 端点。

例如：我们可以在每个服务的末尾，通过追加 HTTP/health 的参数，以返回各个服务实例、主机、连接和算法逻辑等方面的健康状况。

同时，服务注册中心需要定期调用健康检查的 API 端点，以执行相关的健康扫描任务。

而健康检查的内容则可以包括如下方面：
* 针对特定应用的系统逻辑。
* 主机的状态。
* 连接到其他基础设施或任何服务实例的连接状态。

为业务能力而改变一切

在将单体架构分解成多个微服务的过程中，我们需要根据实际情况遵循不同的设计模式。

## 针对业务能力的独特微服务

微服务的成功应该能够充分体现高内聚和低耦合的特点。因此各种服务需要在抽象出相似功能的基础上，保持低耦合的状态。那么，我们该如何将软件系统分解成为更小、更独立的逻辑单元呢？

我们需要定义微服务的范围，从而支持特定的业务能力。例如，我们可以将组织的内部架构分为技术、营销、公关、销售、服务和运维等不同部门，这些不同的职能部门都可以被看作是各个微服务，而组织本身就是一套系统。

因此，为了保持效率和预估增长，我们需要按照业务能力对系统进行分解，基于各种能力所产生的价值，区分不同的业务领域。

## 围绕相似业务能力的微服务

虽然我们可以按照业务能力分类出各种微服务，但是我们该如何处置那些服务中的通用类呢？在此，我们可以用需要干预的“神类（God Classes）”来分解这些类。

例如，在电子商务系统中，订单是一个共用类，一些诸如订单号、订单管理、订单退货、订单交付等服务都会用到它。因此针对该问题，我们引入了领域驱动设计（Domain-Driven Design，DDD）的微服务设计原则。

在领域驱动设计中，我们使用到了各个子域。这些子域模型应当被预定好功能的范围，即界限上下文（bounded context）。

这些界限上下文作为参数被用来创建微服务，从而克服了通用类的相关问题。

## 刀砍藤蔓的模式

上面我们讨论了对全新单体架构概念的分解，下面我们来看看如何将现有的单体系统转换为微服务架构。在此，我们引入刀砍蔓藤的模式。

由于在 Web 应用中，经常会涉及到不同域里各个服务之间的往返调用，因此刀砍模式非常适用于对域的切分。

在该模式下，虽然系统会出现两个域共用一个相同 URI 的情况，但是一旦某个服务完成了转换，我们就会砍掉其对应的应用程序中的现有版本。而且，此过程会一直持续下去，直到单体系统不复存在为止。

### 针对优化数据库存储的微服务设计模式

就微服务架构而言，其松耦合的特性造就了各个独立服务的部署与扩展能力。

但是由于不同的服务有着不同的存储需求，因此它们可能需要访问那些并非存储在本地的数据。

下面让我们来讨论一些根据不同的需求，所适合采用的主要数据库设计模式。

## 基于服务的单独数据库

在领域驱动设计的原则中，基于服务的单独数据库，是将整个数据库分配给特定的微服务。

因此，我们需要按照服务来事先设计好独享的数据库。也就是说，任何其他的外部微服务都无法访问，其他未分配给自己的数据库里的数据，除非是通过微服务的 API 网关方式。

## 基于服务的共享数据库

如果我们只是将上述独享数据库模式运用到，将单体架构分解成多个微服务的场景中，那么难免会碰到各种麻烦。

因此，我们可以在分解的过程中，对有限数量的服务采用基于服务的共享数据库模式。

而这个数量一般会被限制在 2～3 个，否则对系统的部署、自治性和扩展性有所影响。

## 事件溯源式设计模式

当应用的当前状态发生变化时，我们如何才能确保架构能够按需变更，并根据这些变更实时地产生相应的事件呢？

事件溯源（Event Sourcing）模式，能够根据每个业务实体的状态变化，顺次将新的事件追加到事件列表之中。

在系统中，诸如 Customer 这样的实体会产生许多事件，因此我们可以对实体的当时状态进行“截屏式”事件录入，以便进一步查询或通过自动化的状态调整，来优化负载。

## 命令查询的责任分离（CQRS）

对于基于服务的数据库模式而言，由于访问被限制在了单个数据库之中，因此我们很难达到各种复杂的查询效果。那么我们该如何实现各种基于数据库系统的联合查询呢？

CQRS 模型将单个应用程序分为命令和查询两个部分：
1. 命令部分处理各种创建、更新和删除之类的请求。
2. 查询则用到了物化视图（materialized view），而这些视图是通过事件流来进行更新的。

同时，这些事件又是由事件溯源模式所产生，并标注了数据中的各种变化。

### 针对无缝部署的微服务设计模式

在我们实施微服务时，难免会在服务的调用上碰到问题，因此我们可以采用横切（cross-cutting）的模式来简化工作。

## 服务发现

由于采用了容器技术，IP 地址往往是被动态地分配的。这就意味着 IP 地址会随时发生改变，进而导致服务的中断。此外，用户需要记住每个服务的 URL，而这反而倒退成了紧耦合状态。

为了解决该问题，我们需要通过一个注册表，向用户的请求提供位置信息。服务实例在启动时，能够被注册到表中；而在关闭时，也能被注销。

此法有助于用户找出那些可用来查询的准确位置。此外，注册表通过健康检查，能够确保实例的可用性，进而提高系统的性能。

## 蓝-绿部署


在微服务架构中，一个系统里往往有着多个微服务。如果我们因为部署、或更新版本而停止所有的服务的话，那么长时间的停机势必会影响整体的生产力。

因此，我们需要在设计微服务架构时，通过蓝-绿部署的模式，来避免该问题。

在这个模式中，我们同时有着蓝、绿两套相同且并行的环境。在任一时间点，只有一套环境（如蓝色系统）真实在线，并处理着真实的业务流量。

那么在需要进行新的部署时，我们将应用的最新版本上传到绿色系统中，并将真实对外的路由器切换到绿色系统上，以完成更新。


## 结论

虽然您不一定会在自己的微服务系统中用到上述每一种设计模式，但是这些模式都有着它们独特的应用场景。

作为架构师，对于不同的微服务架构设计模式，您需要从应用的设计阶段到生产环境的维护阶段，持续进行各种评估、审计、测试和实践。相信它们在给您带来一致性标准的同时，也能提高您的应用的整体可靠性。