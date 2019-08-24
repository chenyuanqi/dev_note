

### 测试的本质
不同阶段的业务、不同端的业务、不同类型的业务都需要不同程度、不同方法的测试。那么，测试的目的：  
> 检查产品是否满足需求定义 (包括功能、性能、易用性...)  
> 检查产品是否符合上线要求 (除了需求定义外，可能还包括安全性 / 故障预防 / 数据统计...)  
> 检查产品是否可解决目标用户群的一类问题 (除了上线要求外，还要能实实在在解决用户的问题)  
> 检查产品是否可持续性满足用户群的需求 (除了解决问题外，还要使其心情愉悦 / 满足 /“流连忘返”...)  

**不同阶段业务对测试的需求不同**  

- 0 到 1 的 “创业型” 业务  
0 到 1 的 “创业型” 业务，无论项目的紧急程度，还是工作量，都远远超过成熟期业务。此时不仅需要强大的抗压能力，更需要丰富的经验支持快速业务更迭、功能 / 性能 / 安全性 / 易用性... 等等。相对于成熟型业务 90% 都在做回归型测试，新型业务不仅要去拿出足够的时候去支持回归型测试、更要去保障业务线测试 (简言之，新型业务量～=2 倍以上的成熟型业务，附带还要干开发联调，第三方沟通，规范制定，方案制定与实践等等方面)。

此时的测试人员，70%~80% 的时间会都在项目测试本身上，加上项目测试本身外的第三方沟通、项目 “后期” 保证、共识 & 流程方面的建设，测试人员几乎没有太多时间学习，code 工具了。

- “半瓶水” 型业务  
此类业务项目的紧急程度，还是工作量介于创业型业务，成熟期业务之间，而且项目规范，实践经验，测试方案... 都有了一定程度的积累。此时业务需要的测试人员，除了测试经验丰富外，还要有推进整体项目趋于成熟的能力，包括：项目共识的流程规范、更加成熟高效的测试方案、更全面的质量运营工作。

此时的测试人员，50% 时间会都在项目测试本身上，50% 时间会在工具、自动化开发，个人成长上面。这可能是最理想的一种状态了。

- 成熟期业务  
此类业务往往属于公司 / 平台长期发展的一块重头戏，盈利性业务，故而业务本身相对来说上线质量远远大于迭代速度了。业务大多数属于 “修修补补”“零零碎碎” 的业务，迭代速度相对较慢 (这里指迭代的工作量)，项目流程规范、测试方案相对来说比较固定。

此时的测试人员，几乎会有 70% 左右的时间用于自身建设、工具研发等等，项目测试压力本身相对较小。

**不同端业务对测试的需求不同**  

- 端上的测试  
包括 APP，客户端。测试类型包括：功能测试、兼容性测试、性能测试、用户体验测试、软件权限、安装与卸载、数据安全性、离线浏览、APP 更新、PUSH 测试、交叉事件测试等等。ps: 此时的端仅指前端 APP，不包括后端实现。

- m 站的测试  
测试类型包括：功能测试、兼容性测试、性能测试、用户体验测试、数据安全性、离线浏览等等。ps: 此时的端仅指前端页面，不包括后端实现。

- web 测试  
测试类型包括：功能测试、兼容性测试、性能测试、用户体验测试、数据安全性等等。ps: 此时的端仅指前端页面，不包括后端实现。

- 纯后端测试  
测试类型包括：功能测试、性能测试、一致性测试、安全测试、数据测试等等。

**不同业务类型对测试的需求不同**   

- 电商类业务  
这种业务涉及订单、交易、物流追踪等等，某一个环节出问题，可能直接流失收益或客户，所以这类业务的测试除了通用的测试经验外，还需要些交易方面经验的积累，能够减少故障的发生，同时能把控交易业务方面的需求。

- 广告类业务  
这种业务往往涉及打点上报、广告排序、广告展示等等方面，通常广告收入是最重要的业务指标。把控提高广告收入的需求评估，是此类业务的重点。

- 数据类业务  
这种业务往往伴随着大数据统计、报表计算、数据呈现等方面，属于数据端的下游。快速高效的通过数据统计满足各个方用户的需求，同时又能从分析数据中给各个用户以更有价值的指导，是此类业务的核心了。

- 金融类业务  
这类业务往往直接和钱打交道，而且业务本身需求金融知识作为支撑，属于背景知识要求较高的一类业务了。当然了，既然和钱直接打交道，这类业务的测试会更加偏重数据计算。

- 社交类业务  
这种业务往往存在若干个角色，并且伴随着若干个角色直接的互动交互。测试重点更加偏重场景的交互，以及每种角色在业务中需求的满足。因而，此类业务测试需要更加注重易用性、用户测试。

- 游戏类业务  
这种业务除了游戏门户网站外，还有具体游戏本身的测试。此类业务更加偏重对目标人群的研究，满足目标人群的心理需求，设法使其精神上得到最大的满足。

- 软硬结合的业务测试  
此类业务包括物联网方向、人工智能方向等等，软件测试不必多说，硬件的测试本身就需要专业的技术背景。个人认为，软硬件结合的业务，大致需要两拨人来进行全面质量把控：   
1） 软件方面测试人员  
2） 硬件方面测试人员  