
　　以目前的时代来说，微前端并不算是一个很新的概念了，微前端的本质就是大型应用的拆分与关联。在我刚开始学微前端的时候，就接触到了如下的概念：比如基座式微应用、自组织式微应用，或者微前端的实现方案比如：路由分发、iframe、应用微服务化、微件化、微应用化等等。如果你刚开始接触微前端的概念，想要学习微前端，这些概念一定会让你感到困惑，甚至有一种无从下手的感觉。本篇内容，就是为了解决这些问题而存在的。希望可以分享一些我在学习微前端过程中的一些感悟和思路。


## 一、微前端的本质


　　其实要说起微前端的本质很简单，就是分类。当某一个“东西”体积、量级开始变得庞大之后，以“某种逻辑”进行分类成了几乎必然的选择。而天下大事，必然是分久必合，合久必分的动态螺旋的状态的。


　　而驱动微前端这个“东西”分类的原因，则在于前端范畴下的用户体验要求和技术能力的提升，二者相辅相成，一方面时代的发展，底层硬件能力的提升，保证了Web软件的飞速发展，同时用户对于新产品的界面、交互、体验等，也随之提高。


　　而基于这样的背景，前后端分离之后，前端项目的体积也愈发庞大。这就导致不得不考虑如何去拆分前端应用以保持良好的项目体验的问题了。好在，后端早就经历了类似的阶段，于是从微服务的概念中衍生出了微前端的概念。


　　而无论是微服务也好，还是微前端也罢，只不过是不同技术领域，通过某些技术手段来分割代码的一种思路。


## 二、微前端技术要点


　　无论我们是在学习某一门技术，或者在应用某一个框架，或者我们在玩一个RPG游戏，往往都有两件事情尤其需要我们去关注：主线与要点。



拿《塞尔达传说：荒野之息》作为一个例子，有很多的主线任务去做，林克最终的目的是去打倒灾厄盖侬，拯救塞尔达公主。而除了主线之外，还有很多其他的游玩内容，比如神庙挑战，比如支线任务，比如地图探索等等。
我们还可以以Vue3的学习作为例子，我们首先要了解的就是Vue3的生命周期，整个Vue3的运行时经历了哪些步骤和核心环节，然后我们再去学一些它的关键API。
换句话说，“点”与“线”才最终组成了一件事情的完整面貌。通过“点”与“线”的链接，形成了我们的知识体系，也就是“面”。
### 1\.微前端拆分思路


　　当我初次涉足微前端领域时，一系列专业术语立刻吸引了我的注意：iframe方案、路由式微前端、微件化、微应用化、NPM方案、动态Script方案、Module Federation等等。这些术语如同微前端世界的关键词，每一个都代表了一种实现微前端的具体技术手段。
面对这些技术点，我最初的困惑是：这些技术点虽然具体，但它们能否构成一个完整的技术方案呢？是否能够作为理论层面的指导呢？我带着这些疑问，开始深入探索微前端的本质。在我的理解中，这些技术点更像是实现微前端的表面应用，而非深层次的理论指导。
直到后来我学到了这样的概念：横向拆分与纵向拆分。
1\.）横向拆分


　　我们先来看下下面的图片。
![](https://img2024.cnblogs.com/blog/1184971/202412/1184971-20241205141952221-1413383652.png)
　　我们从图中可以看到，整个页面由三部分构成，分别是页头页脚、轮播图和官网详情展示，这是一个很常见的官网页面。但是它却是由三个团队协作开发完成并将输出结果组装在一个页面上的。这种方法提供了很大的灵活性，给我们在不同的视图中复用微前端提供了可能。
在我个人的理解中，横向拆分更倾向于模块化，特别是在面向消费者（ToC）的项目中应用。试想一下，像腾讯视频、爱奇艺这样的视频播放网站，它们的核心功能，比如视频播放和视频展示，通常都具备功能完善、内容丰富、多页面复用等特性。这些特点使得它们非常适合通过横向拆分的方式，实现微前端架构的优化。
换个角度来看，实际上横向拆分的概念，在第一章节中我就已经提前提及了，那就是模块化。我们可以将一个或多个核心功能视为一个模块，这样它们就可以灵活地应用到整个网站需要的各个部分。
　　横向拆分特别注重业务功能的复用性以及网站整体的搜索引擎优化（SEO），因为对于面向消费者（ToC）的项目来说，SEO是一个必然的需求。
由于需要组合多个模块，并且要对网站的SEO进行技术优化，同时还要明确划分不同团队的责任界限，横向拆分在技术实施和团队协作方面，无疑面临着更加严峻的挑战。
2）纵向拆分


我们还是先看一下图。
![](https://img2024.cnblogs.com/blog/1184971/202412/1184971-20241205142002966-1663956614.png)
　　图中展示了两个页面，它们各自承担着不同的业务职责。我们可以看到，一个是产品详情页，另一个是产品创建页。尽管它们的业务功能不同，但它们的头部导航和侧边导航部分是共用的。这种由一个团队负责整个页面的设计和开发的方式，被称为纵向拆分。在这种情境下，如何合理地拆分业务，可以借助领域驱动设计（Domain\-Driven Design, DDD）作为指导思想。
如果你经常写单页应用，纵向拆分其实要比横向拆分更容易理解，也更容易实施。
不知道大家还记不记得这样一句话，叫做前端在一定程度上是天然解耦的。什么意思呢？就是往往，我们在开发分配任务的时候，很少会说，你写一个搜索框，他写一个列表，然后最后组合在一起，而是你写这个页面，他写那个页面，最终在项目合并的时候也不会互相干扰和依赖。而这种场景以及拆分方式，其实更适合ToB的后台管理系统、SaaS类项目。
这样的项目往往业务领域明确，范围清晰，但是业务逻辑和场景则多变和复杂。通过纵向拆分可以聚合针对某一领域理解深刻的开发及产品团队，专注于单一领域，为整个项目的迭代和发展带来更大的优势。
### 2\.限界上下文


　　关于界限上下文，以及如何区分核心子域、支持性子域、通用子域这样的概念我并不想这里过多的讨论，这本书毕竟不是聊领域驱动设计的，如果大家有兴趣，完全可以自行学习，我更想和大家聊一聊的是，限界上下文这个概念，在微前端领域处在一个什么位置，有什么作用。


　　限界上下文按照我的理解，其实就是要按照什么样的逻辑来拆分微前端，比如说，我们可以按照业务范畴来拆分。在一个通常的SaaS系统里，可以拆分为应收应付、订单创建、产品、仓储等等子系统。而在一个ToC的网购软件或者视频网站上，则可以按照其复用性或功能性来拆分，比如购物车、产品列表、产品详情，或者视频播放器、视频详情等等。
但是很多时候，可能有些理论并不是那么有用，举个例子，现在有一个老旧的SaaS项目，整个目录结构和业务领域压根不搭边，全都是平铺出去的，但是现在领导希望可以应用新的技术，把老旧的项目也整合进来，进而开发新的业务，达到项目上的大一统。还记不记得之前我们聊过微前端的使用场景，增量升级那个，现在我们就要来做这样一件事。
　　那怎么办呢？如果我拆分老旧的系统，区分其所归属的业务领域，会花费我们大量的时间来分离子系统，本来老旧的项目很稳定了，也无需什么更改，结果你要是这么一搞，不知道要给测试、开发带来多少问题，所以，我们希望老旧系统不动，直接用Nginx反向代理或者iframe就好了。没错，这是一个很好的选择，但是同时带来的问题就是，你遵循了领域驱动设计了么？很显然并没有，但是这却是必要且正确的错误选择。
　　上面举得这个例子想要告诉大家的就是，理论是指导实践的必要工具，但是很多时候，我们未必一定要遵循理论。
### 3\. 组合


　　组合的概念，实际上指的是我们要如何拼凑及加载微前端界面，比如我们熟知的qiankun、wujie等微前端框架，都属于客户端组合的范畴。除了客户端组合，还有服务器端组合以及边缘侧组合。
　　我们先来了解一下这样一个流程，当我们在浏览器中看到界面的时候，在这之前都发生了什么。很简单，就是从服务器获取界面所需的资源，比如html、js、css这些，然后经过浏览器的解析渲染，最终呈现出界面。但是为了更快的获取资源，在客户端和服务器中间，往往可能还有一个CDN用来存储前端的静态资源，从而加快获取速度。
那么我们再来理解一下关于组合的三种方式：
* 客户端组合：其实就是通过js在客户端运行时加载微前端及其相关功能，所有的事情都是在客户端完成的。
* 边缘侧组合：我们会在CDN层对视图进行组合，通过一种叫做ESI的类似于XML的标记语言可以达成这样的目的。
* 服务器组合：其实说白了，就是类似于SSR，在服务器的运行时或者编译时进行组合，拼凑微前端从而生成最终的视图结果后，返回给前端完整的HTML，这样做，最大的优点是提升客户端的体验以及提供良好的SEO效果。


### 4\. 路由


　　在现代单页应用如此广泛普及的情况下，想必大家对于客户端路由一点都不陌生了。在大多数情况下，我们选择怎样的微前端组合方式，就会对应的使用怎样的微前端路由方式。当然，这种情况不是绝对的，就比如假设我们选择服务器组合，但是服务器要承受的压力太大，就可以把路由分发的事情交给CDN来做，也就是边缘侧路由。
　　这里我要稍微强调一下， CDN路由或者CDN组合是属于边缘侧的一种方案，但是边缘侧并不仅仅只有CDN一种。边缘计算是一种分布式计算范例，它将计算资源和数据存储接近最终用户的位置，以便提供更低的延迟和更高的性能。换句话说，为了增强客户端或者减轻服务器压力的一些中间或额外的基础设备所造成的增强性能力，都可以算作边缘侧。
　　无论是哪种方法，在实际操作中，我们并不局限于单一的选择。也就是说，我们既可以在客户端进行组件的组合，也可以在服务器端进行部分组合。同时，我们既可以实现客户端路由，也可以针对某些特定的路径，直接从服务器端请求数据或者通过内容分发网络（CDN）获取数据。这种灵活性使得我们能够根据项目的具体需求和特点，选择最合适的实现方式。
### 5\. 通信


　　从微前端的定义上来讲，其实我们并不需要子系统之间的通信，因为微前端的定义就是独立自治，它不应该和其它子系统产生任何理论上的通信和关系。但是我也多次强调，理论很多时候并不是那么好用，我们也无需教条于理论。
　　虽然微前端的定义如此独立，但是微前端之间的通信在大多数场景下都是十分必要的。比如登录状态的共享，子系统间信息的传递等等。
　　如果你是在同域的情况下，完全可以使用WebStorage的SessionStorage、LocalStorage或者cookie来进行登录状态的共享。哪怕你跨域了我们也可以使用postMessage进行通信。
　　但是，假设，你跨域了一个并非自主开发的项目，也就是你想要接入别人的跨域的项目，还无法获取源码或者私有部署，那，你还需要通信么？
　　给大家开了一个小小的脑洞，我们继续哈。除了以上的方案外，我们也可以利用现成的框架如wujie、qiankun等来进行现成的开箱即用的通信手段。
　　当然，除了这些我们也可以自己实现一个简易的EventBus来进行数据的共享。还有一种我们常用的选择，也就是通过URL的query来进行通信，这种方案简单实用，几乎没有什么技术难度，但是如果你要想做一个通用的URL传递参数的方法，在微前端中进行实践，也还是要多思考一些的。
　　最后，我们来总结下，在微前端中进行通信都有哪些可行的方案。
1. WebStorage
2. Cookie
3. PostMessage
4. EventBus
5. 自定义事件，即发布订阅模式
6. URL
7. 其它：比如window.name等。
8. Vuex、Redux等状态管理工具。


### 6\. 隔离


　　隔离这个话题并非是随着微前端概念的出现才诞生的，它一直存在，并且一直困扰着开发者们。我们都希望拥有一个干净、不受干扰的环境来发挥我们的技术才能。然而，JavaScript变量可能会被后来的代码覆盖，CSS选择器的使用可能无意中降低了其他样式的优先级，这样的问题确实令人头疼。
　　于是js从IIFE发展到规范化的ES Module，css也在某些特定的领域拥有了自己的scope。那么在微前端的范畴下，要如何应对js和css的隔离问题呢？
　　在原生的背景下，我们都是基于iframe或者webComponent作为微前端实践的选型，从而从根本的角度上进行js和css的隔离，再去解决因为选型所带来的某些副作用，这种方案就是wujie微前端框架的隔离解决方案。
　　当然，除了原生方案，我们还可以使用如BEM等命名空间的CSS命名方式来隔离CSS、通过shadowDOM来原生隔离CSS和HTML。
　　关于JS的隔离，方案其实有很多，比如Webpack Module Federation、各种微前端框架等等，但是他们实现的核心，仍旧离不开基本的原理。就拿JS来说，你到了运行时的环境，要隔离的话，无非就是模块化或者IIFE等基本的JS隔离方案。

## 三、微前端方案浅析



　　微前端本质上来说是一个技术架构思想，基于我们前两章对于微前端的优缺点、微前端的拆分方案等的了解，我们对微前端已经有了一个具体一些的认识。我们了解了微前端的优缺点，微前端的适用场景与实现要点等等。但是这些内容只能算是形而上的理论或者原则，它的意义是指导具体的实践，而在具体的实践中，我们往往需要一些具体的方案或者手册来指导。
本章，我们就来依据市面上一些微前端方案，去实现一些对应方案的简单例子，深入的去理解理论与实际的交界是什么样的。
目前来说，微前端的实现方案大体有如下几种：
1. Router（路由式）
2. Iframe（前端容器化）
3. Web Component（应用组件化）
4. 微服务化
5. 微件化（组件式）
6. 微应用化（组合式）


　　前三种我们很好理解，就是基于某种Web核心能力作为支持，来实现我们的微前端方案，通过这些能力再配备一些技术我们就可以做到不错的微前端体验。但是后三种方案，并没有说明要使用哪种技术点作为实践的核心能力，而更像是一种针对某一个“能力”的描述，即模糊，又不具体，需要我们花费一些时间去了解它们的区别。
　　在我们不了解某一个知识点并且没有太好的切入点时，我们可以尝试从它的名称作为切入点。
　　微服务化听起来似乎与服务器密切相关，其核心确实与后端的微服务紧密相连。关键在于实现“完全的独立性”，即从开发到部署，再到构建和运行，每个服务都是完全独立的，与其他应用没有直接的联系。最终，通过“模块化”的方式将这些独立服务组合成一个完整的应用集合。微服务化的最终目标是提高整个系统的可维护性和扩展性，同时减少开发团队之间的耦合。要牢记的关键点是“独立”和“降低耦合”。通过这种方式，每个团队可以专注于自己的服务，而不必过多担心其他服务的影响，从而提高开发效率和系统的灵活性。
　　而微件化从名称上来说，核心在于“微件”。微件（widget），指的是一段可以直接嵌入在应用上运行的代码，它由开发人员预先编译好，在加载时不需要再做任何修改或者编译。换句话说，微件就是一段已经完备的随时可以拿来使用的一段代码，这段代码可以以任何形式存在，目的是“拿来即用”。
　　微应用化则是指把业务或者需求拆分成一个有一个独立的应用，在构建时可以组合成一个完整的业务应用。因为要有页面上代码的组合，所以这些微应用需要依赖于相同的框架环境，没办法混合多个框架。

## 四、微前端之道


　　上面我们只是简单的介绍了一下微前端相关的基础理论概念，限于篇幅，不再赘述。


　　如果大家有兴趣学习微前端相关的知识，大家可以在文末的链接，在京东购买我新出版的关于微前端相关的偏入门方面的《微前端之道》这本书。


　　本书只有极少的必要的概念讲解，大约百分之二十左右（前两章），从第三章起，就会开始实现各种微前端方案的简单例子。


　　后面的章节会分为两个部分，第一部分会带大家一起实现一个完整Saas项目，其中包括了从开发到部署服务器的所有步骤，包括Jenkins、Nginx、Docker的简单使用等等，打破大家对服务器陌生的壁垒。


　　然后会带大家实现微前端的NPM方案、动态Script方案，以及现代各种微前端框架的简单使用等等。


　　这本书理论和实践结合，没有通篇枯燥的理论，没有脱离实际，也没有晦涩难懂的深度，这本书很适合作为微前端的入门读物。


　　目前市面上的微前端书籍并不多，我个人觉得唯一有价值的就是《微前端实战》，所以在结合个人经验和学习的路径，最后写了这本跟微前端有关的书籍。希望可以给大家带来一些必要的帮助。


![](https://img2024.cnblogs.com/blog/1184971/202412/1184971-20241205102352656-197446289.jpg)


京东链接：[https://item.jd.com/14348331\.html](https://github.com)


当当网：[https://product.dangdang.com/29823513\.html](https://github.com):[milou云加速器官网](https://jiechuangmoxing.com)


