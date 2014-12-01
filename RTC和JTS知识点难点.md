#记录RTC/JTS的知识点和难点
###RTC(Rational Team Concert)
 - 作为一个用户，您具有自己的私有存储库工作空间，用于存储您所作的变更
 - 在 Eclipse 中，此沙箱的初始缺省值与您的 Eclipse 工作空间是同一目录。
 - 您还可以直接从另一个存储库工作空间中接受变更，从而允许团队成员之间以细颗粒度方式共享变更。例如，两个团队成员可以协作完成细微错误的修订；或者，如果某个成员启动了某项变更，但是去度假了，那么另一个团队成员可以继续完成他的工作，稍后再交付变更。
 - 源文件库是在稳定增长的变更集基础上构建的，每个变更集都以之前的所有变更为基础。**每个存储库工作空间或流都基于一系列的变更集。**
 - Jazz Team Server 提供了基本服务，例如用户管理和许可证管理，这些服务使多个 CLM 应用程序能够作为单一逻辑服务器一同工作
 - Rational Team Concert™ 是一个基于可伸缩可扩展平台的团队协作工具。Rational Team Concert 使用“变更和配置管理”(CCM) 应用程序，来提供集成开发项目任务的功能，包括迭代规划、过程定义、变更管理、缺陷跟踪、源代码控制、构建自动化以及报告
 - 缺省情况下，Jazz™ Team Server 上的 Rational® 构建代理程序每 15 秒检查一次构建状态。
 - zFile如果 Line delimiter 未设置为 Platform，那么会将文件以 UTF-8 格式传送到 z/OS。UTF-8 格式不可通过编译器或绑定程序进行读取。
 - 源代码数据缺省情况下，每一个小时会自动扫描一次数据流。这些自动扫描只包括自上次扫描后已变更的文件。运行依赖关系构建时，Rational Team Concert 会使用这些源代码数据来确定在更新代码后应该重建的源代码。如果要运行依赖关系构建，那么必须通过针对您的源代码运行源代码数据扫描程序来收集此数据，并且必须启用此扫描。
 - 在存储库工作空间中，将收集相关的变更以创建变更集，这使您能够通过单一操作交付多个文件和文件夹中的变更。
 - Jazz Source Control 图标 Rational Team Concert 源代码控制 图标
 - Rational Team Concert™ 源代码控制 将可版本化的项（文件和文件夹）组织成组件和流，并提供了工作空间以便您在其中查看和修改文件及文件夹内容。
 - Rational Team Concert™ 源代码控制 使用托管于服务器上并可供客户机通过 URL 访问的安全存储库。此存储库用于存储帮助您管理变更流向的对象，例如流、工作项和工作空间。另外，它还存储受控工件。
 - 存储库是由 Jazz™ Team Server 管理的安全数据库。它存放支持团队过程所需的所有对象，包括组件、工作空间和团队区域。客户机通过 HTTP 连接到存储库。
 - 文件版本通过文件内容、属性、文件名和所在文件夹等方面的变更进行区别。您可以添加、移动、重命名、修改和删除文件。文件夹版本通过文件夹属性、名称以及在文件夹层次结构中的位置等方面的变更进行区别。您可以添加、移动、重命名和删除文件夹。
 - 当您创建快照时，将为工作空间中尚不具备基线的任何组件隐式创建基线。有一个选项是始终创建基线（即使已经存在基线）。
 - 变更集是 Rational Team Concert™ 源代码控制 中的基本变更单元。任何工作空间、组件或流的内容都可以表示成一组变更集，其中的第一个变更集就是先前检入初始项目集合时创建的变更集。存储库工作空间中的每个组件都包含零个或多个活动变更集。
 - 如果您不想添加到 Rational Team Concert 源代码控制 的资源显示在已打开的变更集或者未解决文件夹中，请右键单击该资源，然后单击忽略。该资源将被添加到 .jazzignore 文件，这使该文件成为当前变更集的组成部分。
 - 个人构建会构建存储库工作空间与最近一次团队构建之间存在的差异
 - you can select the "Perform full minimum load" option. If you select this option, the build code loads the source code and dependent files from the personal repository workspace you specified in the Request Build editor.
 -  Full minimum load option loads all files needed to build modified and impacted programs to personal sandbox
 -  Complete changeset之后是不能再做任何变更的
 - RTC 本地Workspace的路径： C:\Users\Administrator\

###JTS (Jazz Team Server) 
- 拓扑：典型安装由 JTS以及一个或多个 Web 应用程序组成：质量管理 (QM)、变更和配置管理 (CCM) 和需求管理 (RM)。可以将这些应用程序部署在同一应用程序服务器上，以进行小规模评估；也可以将它们部署在不同的应用程序服务器上，以获取更大的可伸缩性和灵活性以满足将来的扩大。数据仓库有一个数据库，并且每个应用程序（其中包括 Jazz Team Server）都有一个数据库。
- JTS和每个应用程序都具有自己的安装子目录，嵌套在 JazzTeamServer\server\conf 下。包括admin、ccm、jts、qm 和 rm 的相应子目录。这些子目录包含该特定应用程序的数个配置文件，以及每个应用程序的 Derby 数据库。尤其是，qm 目录还包含测试执行适配器和迁移实用程序等
- Apache Tomcat 已安装在 JazzInstallDir/server/tomcat 目录中。Web 应用程序（jts.war、admin.war、ccm.war、qm.war、rm.war 和 clmhelp.war）安装在 Apache Tomcat 目录 webapps 中。
- 单个存储库中可以包含多个项目区域以及与每个项目区域相关联的工件。存储库中的每个项都具有唯一的标识(UUID)，您可以使用此标识作为键来检索该项。存储库由关系数据库提供支持，在存储库中创建、更新和删除项的操作只能通过服务器端机制完成。
- 备份复原JTS以及Derby数据库的步骤：
		    
		停止JTS
		执行repotools-jts -suspendIndexer 来暂挂存储库索引编制服务
	    JazzInstallDir/server/conf/jts/indices 
	    JazzInstallDir/server/conf/application/derby/repositoryDB
	    JazzInstallDir/server/conf/jts
	    JazzInstallDir/server/tomcat/conf
	    JazzInstallDir/server/tomcat/bin
	    执行repotools-jts -suspendIndexer来暂挂存储库索引编制服务
 

