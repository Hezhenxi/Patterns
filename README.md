# 设计模式-重构 & Spring源码阅读 :see_no_evil:

## 目录

<a name="3060-1621846615933"></a><a name="aikf-1703092288954"></a>[源码阅读快捷键](#y7rk-1696756330756)

<a name="xwny-1703092288956"></a>[看方法实现的两种方法](#l9ks-1696756330757)

<a name="mtbf-1703092288959"></a>[普通方法：Ctr + 鼠标(B)  / Ctr +Alt +鼠标   ](#xiud-1645584792124)

<a name="olb0-1703092288961"></a>[抽象方法：Ctr +Alt +鼠标  ](#dqnd-1645584889594)

<a name="fnze-1703092288963"></a>[查看方法用例](#iulz-1696756330758)

<a name="rfo5-1703092288965"></a>[Ctr +鼠标  查看方法用例 useage](#nb1b-1645584977418)

<a name="o05j-1703092288967"></a>[类Structure ](#ybdy-1696756330759)

<a name="0l6u-1703092288969"></a>[-ctrl+H Hierarchy层级图    ](#xygl-1699829959815)

<a name="xmde-1703092288971"></a>[-ctrl+alt+U Diagram结构图表](#abj6-1699830019023)

<a name="xois-1703092288973"></a>[▁▁▁▷ 继承/泛化 Animal -name:string +eat():void ; Bird -name:String +fly():void; Lion -name:String +run():void](#p8ep-1702238726050)

<a name="iiip-1703092288975"></a>[----▷ 实现  University +educate():void; Peking +educate():void; Tsinghua +educatie():void](#i2sh-1702238726051)

<a name="zy0l-1703092288977"></a>[▁▁▁◆ 组合 Body -brain:brain ; Brain -name:String +thinking():void ](#bns2-1702238726052)

<a name="fc9f-1703092288979"></a>[▁▁▁◇聚合 School -terachers:List<Teacher> ; Teacher  -name:String](#bdnt-1702238726053)

<a name="3kia-1703092288981"></a>[------>依赖   Programmer -name:String  +coding(Computer c) void  ;    Computer +code():void](#bldx-1702238726054)

<a name="qs8d-1703092288983"></a>[▁▁▁▁>关联 ▁▁▁双向关联 Teacher -students:List<Student> +teach():void ; Student -teachers:List<Teacher> -courses:List<course> +study():void; Course name:String](#qtkf-1702238726055)

<a name="xhmb-1703092288985"></a>[善用UML图 统一建模语言 （类图、方法调用时序图）](#xgvz-1699829941205)

<a name="h0xy-1703092288987"></a>[=== 重构必备快捷键===](#u4qd-1699827590539)

<a name="rcso-1703092288989"></a>[Alt + Delete Safe Detele(安全删除，可用在方法上进行快速删除)](#7jgm-1699827592479)

<a name="puee-1703092288991"></a>[Shift +F6重命名-](#zbnc-1699827592481)

<a name="u5k4-1703092288993"></a>[F5/F6复制/移动元素](#lcsh-1699827592483)

<a name="5d6e-1703092288995"></a>[Ctrl + Alt +M抽取方法 Extract Method](#svos-1699827592485)

<a name="q9ry-1703092288997"></a>[Ctrl + Alt+ C抽取常量](#i62k-1699827592487)

<a name="b3tl-1703092288999"></a>[Ctrl +Alt+ F抽取字段](#3lvw-1699827592489)

<a name="lpii-1703092289001"></a>[Ctrl + Alt+P抽取参数](#8vae-1699827592491)

<a name="erxy-1703092289003"></a>[Ctrl + Alt+ V抽取变量](#0hnv-1699827592493)

<a name="b5wo-1703092289005"></a>[Ctrl + Alt+Shift +P抽取函数参数](#ljc1-1699827592495)

<a name="3cff-1703092289007"></a>[Ctrl + Alt+Nlnline(转换为内联、方法链形式的调用，抽取方法的反操作)](#rltn-1699827592497)

<a name="eucj-1703092289009"></a>[Ctrl + F6Change Signature(修改方法、类的签名，含参数、返回值类型等)](#8n32-1699827592499)

<a name="nozi-1703092289011"></a>[Spring源码](#2yjy-1701954398769)

<a name="clmq-1703092289013"></a>[AOP](#yskl-1701954404974)

<a name="qrbj-1703092289015"></a>[.基本概念(面相切面)](#ol57-1701954646926)

<a name="vrag-1703092289017"></a>[.底层原理(JDK动态代理 CGLIB动态代 理)](#5vn0-1701958435935)

<a name="6bu5-1703092289019"></a>[1.JDK动态代理 -接口](#p22c-1702323312832)

<a name="w2ki-1703092289021"></a>[2.CGLIB动态代理 -抽象类、类](#fl6z-1702323317995)

<a name="cqiq-1703092289023"></a>[.底层原理(JDK动态代理实现)](#t5yl-1701959474530)

<a name="nis2-1703092289025"></a>[1.动态代理构建代理对象](#8jra-1702323371005)

<a name="buya-1703092289027"></a>[2.使用动态代理对象](#uiso-1702323377901)

<a name="payp-1703092289029"></a>[.AOP操作术语(连接点.切入点.通知/增强.切面)](#ry4r-1702154401445)

<a name="alvz-1703092289031"></a>[.AOP操作-AspectJ注解1](#7pzc-1701959416099)

<a name="blua-1703092289034"></a>[.AspectJ注解2](#7yy9-1701959441941)

<a name="qumn-1703092289036"></a>[1.相同切入点抽取(@Poincat)](#65vp-1702238013766)

<a name="e2px-1703092289038"></a>[2.有多个增强类，设置增强类优先级(@Order)](#asry-1702238027465)

<a name="naht-1703092289040"></a>[.Aspect配置文件(xml)](#2l0f-1702238022847)

<a name="lqfy-1703092289042"></a>[Spring事务](#rft6-1701954414068)

<a name="2kx1-1703092289044"></a>[.事务概念(数据库事务的抽象)](#snhq-1702241780386)

<a name="feoa-1703092289046"></a>[1.对数据库事务的抽象](#wutq-1702514681562)

<a name="xvkd-1703092289048"></a>[2.声明式事务](#6cfq-1702514708257)

<a name="lwn2-1703092289050"></a>[3.编程式事务](#xl9m-1702514717169)

<a name="h5fb-1703092289052"></a>[4.事务传播行为](#wvpz-1702514725302)

<a name="mmy6-1703092289054"></a>[.事务场景引用(银行转账)](#gg1m-1702241805374)

<a name="wj6g-1703092289056"></a>[.事务管理(service层)](#rna6-1702241818624)

<a name="pqc6-1703092289058"></a>[.底层原理(TransactionInterceptor)](#zsml-1702156135978)

<a name="6qb7-1703092289060"></a>[.事务传播(事务的交互)](#9rmz-1696756330760)

<a name="0dqs-1703092289062"></a>[.事务隔离级别(同mysql)](#xcrx-1702156171784)

<a name="sjvo-1703092289064"></a>[.事务参数](#nj45-1702517125369)

<a name="hdqt-1703092289066"></a>[1.timeout:超时时间](#agn5-1702323504347)

<a name="2uag-1703092289068"></a>[2.readOnly:是否只读](#6xui-1702323546562)

<a name="b6du-1703092289070"></a>[3.rollbackfor:回滚;](#nnjk-1702323572146)

<a name="lftf-1703092289072"></a>[4.noRollbackor:不回滚;](#jbnx-1702323577652)

<a name="ygex-1703092289074"></a>[.事务失效](#ges0-1702295839157)

<a name="vtg1-1703092289076"></a>[1.自动提交:事务执行SQL,异常后自动提交](#oz7x-1702323587855)

<a name="7mgq-1703092289078"></a>[2. try-catch捕获异常:消费掉异常](#xh3y-1702323627701)

<a name="gx8s-1703092289080"></a>[3.不受检查异常:非RuntimeException及子类](#uzqi-1702323653445)

<a name="kdpo-1703092289082"></a>[4. Propagation属性设置错误:事务交互嵌套事务中导致事务失效](#cxmb-1702323660680)

<a name="qgjt-1703092289084"></a>[5.并发问题:死锁](#0a5i-1702323666422)

<a name="j7sn-1703092289086"></a>[6.错误选择数据库隔离级别问题:READ_UNCOMMITTED](#zepp-1702323671358)

<a name="isih-1703092289088"></a>[7.分布式事务问题:](#m69p-1702323677953)

<a name="oorm-1703092289090"></a>[8.长事务:](#etkm-1702323684344)

<a name="130y-1703092289092"></a>[注解](#peq9-1702156163512)

<a name="xieg-1703092289094"></a>[循环依赖](#zpsm-1702155028191)

<a name="qjff-1703092289096"></a>[设计模式-重构](#gvfv-1702236185333)

<a name="4mee-1703092289098"></a>[通用原则](#w0cs-1696756330761)

<a name="vrjt-1703092289100"></a>[-代码 开放/封闭 原则，](#aj9d-1699828474925)

<a name="otf7-1703092289102"></a>[- 多用组合，少用继承](#6bga-1649502279787)

<a name="ctzk-1703092289104"></a>[-依赖倒置原则-面向接口编程](#ub5i-1649502231177)

<a name="7x80-1703092289106"></a>[-依赖抽象，不要依赖具体类](#on9f-1649502485850)

<a name="eq0h-1703092289108"></a>[-独立需要变化和不需要变化的代码](#dl5h-1702325051758)

<a name="gu4j-1703092289110"></a>[-交互对象之间要松耦合设计](#6orr-1702325088901)

<a name="fzx2-1703092289112"></a>[-一个类应该只有一个引起变化的原因(单继承？)](#van1-1702325113068)

<a name="z0g0-1703092289114"></a>[-最少知识原则，只和密友谈话](#vmrt-1702325157809)

<a name="st3k-1703092289116"></a>[-别调用我们，我们会调用/通知你](#fgkj-1702325179787)

<a name="ulfm-1703092289118"></a>[工厂模式(产品接口，工厂接口)](#dout-1702325047416)

<a name="wof1-1703092289121"></a>[客户端代码可以通过选择不同的工厂来创建不同的产品](#cpml-1702332761576)

<a name="cypm-1703092289123"></a>[1.产品接口  具体产品1 具体产品2](#qfre-1702333590011)

<a name="8p3l-1703092289125"></a>[2.工厂接口  具体工厂1-构造产品1  具体工厂2-构造产品2 ](#lx6u-1702333615242)

<a name="tx1v-1703092289127"></a>[3. 选择不同的工厂创建不同的产品](#mhgn-1702333854385)

<a name="7fga-1703092289129"></a>[单例模式](#jm2n-1696756330762)

<a name="vzmq-1703092289131"></a>[装饰器模式(组件接口，抽象装饰器实现组件接口)](#hzzm-1696756330763)

<a name="1hea-1703092289133"></a>[客户端代码可以选择性地使用装饰器来包装具体组件](#8nqr-1702334948103)

<a name="7t6i-1703092289135"></a>[1.组件接口，Concrete具体组件1  具体组件2](#vc2u-1702333931030)

<a name="zkbs-1703092289137"></a>[2.抽象装饰器实现组件接口  具体装饰器1  具体装饰器2](#rmxw-1702334202292)

<a name="fad7-1703092289139"></a>[3.使用具体装饰器包装具体组件  Component decoratedComponentA = new ConcreteDecoratorA(componentC);](#jbhr-1702334336845)

<a name="lv6z-1703092289141"></a>[装饰器和代理的区别：](#ph56-1696756330764)

<a name="72ng-1703092289143"></a>[1.装饰器模式关注于在一个对象上动态地添加方法，而代理模式关注于控制对对象的访问。](#psj7-1677978919986)

<a name="e6ps-1703092289145"></a>[2.装饰器模式是为了增强原有对象的功能，而代理模式是为了施加控制或者提供额外的服务。](#vdgu-1677978921450)

<a name="q1ot-1703092289147"></a>[3.装饰器模式中，装饰类和目标类是解耦的，装饰对象不感知目标对象的存在，由调用方控制对目标对象的引用。而代理模式中，代理类和目标类是耦合的，代理对象控制对目标对象的引用。](#ecno-1677978921452)

<a name="cb9n-1703092289149"></a>[4.装饰器模式通常只有一个装饰类，而代理模式可以有多个代理类。](#vany-1677978921454)

<a name="kaaa-1703092289151"></a>[5.代理类注入的是具体目标类，强耦合，多个目标类需要写多个代理类-静态代理；动态代理动态生成代理对象，无需为每个类都手动编写代理类）](#k4d4-1702335689176)

<a name="yzkt-1703092289153"></a>[6.抽象装饰器注入的是组件接口，调用方控制对目标组件对象们的引用，灵活组合](#rgbn-1702336021986)

<a name="hzgq-1703092289155"></a>[代理模式(主题接口，代理类实现主题接口)](#cocv-1702335104756)

<a name="iy97-1703092289157"></a>[客户端通过代理类对方法进行增强](#zmqj-1702335858368)

<a name="bvcb-1703092289159"></a>[1.主题接口，具体主题](#ickc-1702335156454)

<a name="hs8v-1703092289161"></a>[2.代理类实现主题接口，并注入具体主题](#he1l-1702335163013)

<a name="0grb-1703092289163"></a>[3. 对具体主题进行增强](#nipw-1702335663657)

<a name="l2c9-1703092289165"></a>[动态代理，动态生成代理对象](#wtvy-1702336278237)

<a name="bpgz-1703092289167"></a>[1.代理类实现InvocationHandle接口](#3hi4-1702336292130)

<a name="6wil-1703092289169"></a>[2. 注入为Object类，利用反射执行Object方法，返回代理对象](#8j5x-1702336513852)

<a name="wqqn-1703092289171"></a>[3.对具体主题进行增强](#l9oy-1702336337485)

<a name="f7qp-1703092289173"></a>[适配器模式：](#srgw-1696756330765)

<a name="uysz-1703092289175"></a>[1.220V接口，110V接口](#eeir-1703089634191)

<a name="ldnl-1703092289177"></a>[2.适配器类实现220V接口，并注入110V接口](#pvyr-1703089725206)

<a name="gjlx-1703092289179"></a>[3.将220V转换为110V接口](#1ovh-1703090953107)

<a name="tfi7-1703092289181"></a>[策略模式:(常用替换if else）](#y76p-1696756330766)

<a name="xeqf-1703092289183"></a>[1.环境类（contex）:注入策略接口， excute执行逻辑 ](#medy-1703092035603)

<a name="c1ei-1703092289185"></a>[1.策略接口](#idgz-1678386529147)

<a name="lsd9-1703092289189"></a>[2.具体策略：策略接口多种实现类](#1imw-1678386551525)

<a name="w8ue-1703092289191"></a>[AOP用到的设计模式](#xa1i-1699829834311)

<a name="imej-1703092289193"></a>[-代理模式：](#2rlp-1699829827091)

<a name="ww8d-1703092289195"></a>[-观察者模式：](#ujdc-1699829827427)

<a name="chwv-1703092289197"></a>[Mybatis动态代理源码解析](#toz8-1701952321001)

<a name="ziwt-1703092289199"></a>[编程术语](#tyc5-1702154664221)

<a name="qsvc-1703092289201"></a>[脏数据](#9inw-1702516779934)

<a name="i68d-1703092289203"></a>[.未提交的数据: 脏读](#vtbf-1702517147469)

<a name="ldjh-1703092289205"></a>[.已提交的数据但未持久化: Innodb BufferPool脏页刷入磁盘](#doto-1702517147470)

<a name="iuyg-1703092289207"></a>[.数据冲突: 同时修改被覆盖](#4yp9-1702517147471)

<a name="inks-1703092289209"></a>[.数据格式错误: DB导入数据格式错误](#4nkl-1702517147472)

<a name="o9ma-1703092289211"></a>[.缓存不一致: DB缓存不一致](#weer-1702517147473)

<a name="go02-1703092289213"></a>[自旋(循环执行,不阻塞自己)](#7qhf-1702516793084)

<a name="obfh-1703092289215"></a>[.自旋锁(循环检查锁是否释放)](#heoy-1702516915331)

<a name="ciyn-1703092289217"></a>[.自旋等待(反复检查条件是否满足)](#wfj6-1702516920265)

<a name="da5k-1703092289219"></a>[CAS(compare-current & swap-next)](#mfpx-1702516831964)

<a name="rbmm-1703092289221"></a>[《改善既有代码的设计》](#7xtw-1696756397430)



<a name="cgi3-1696756330752"></a><a name="y7rk-1696756330756"></a>**源码阅读快捷键**

<a name="l9ks-1696756330757"></a>**看方法实现的两种方法**

<a name="xiud-1645584792124"></a>**普通方法：Ctr + 鼠标(B)  / Ctr +Alt +鼠标**   

<a name="lchj-1699830145011"></a>查看方法声明，**PS:普通方法，可被继承重写，查看重写方法也用implement**  

<a name="dqnd-1645584889594"></a>**抽象方法：Ctr +Alt +鼠标**  

<a name="j1hg-1699830114755"></a>查看实现 implement  

<a name="iulz-1696756330758"></a>**查看方法用例**

<a name="nb1b-1645584977418"></a>**Ctr +鼠标  查看方法用例 useage**

<a name="ybdy-1696756330759"></a>**类Structure** 

<a name="st0g-1645585735206"></a>**>Object** 下的方法为重写方法  **PS： 源码中重写/覆盖父类方法会省略@override**

<a name="plpl-1645586157976"></a>**>Interface**   下的方法为为抽象方法   **PS: 不一定为接口，>Object 和 >Interface 可能是同一个类，不过分重写父类方法 和 实现抽象接口   如 BufferedWriter extends Writer**

<a name="xygl-1699829959815"></a>**-ctrl+H Hierarchy层级图**    

<a name="abj6-1699830019023"></a>**-ctrl+alt+U Diagram结构图表**

<a name="p8ep-1702238726050"></a>**▁▁▁▷ 继承/泛化 Animal -name:string +eat():void ; Bird -name:String +fly():void; Lion -name:String +run():void**

<a name="i2sh-1702238726051"></a>**----▷ 实现  University +educate():void; Peking +educate():void; Tsinghua +educatie():void**

<a name="bns2-1702238726052"></a>**▁▁▁◆ 组合 Body -brain:brain ; Brain -name:String +thinking():void** 

<a name="bdnt-1702238726053"></a>**▁▁▁◇聚合 School -terachers:List<Teacher> ; Teacher  -name:String**

<a name="bldx-1702238726054"></a>**------>依赖   Programmer -name:String  +coding(Computer c) void  ;    Computer +code():void**

<a name="qtkf-1702238726055"></a>**▁▁▁▁>关联 ▁▁▁双向关联 Teacher -students:List<Student> +teach():void ; Student -teachers:List<Teacher> -courses:List<course> +study():void; Course name:String**

<a name="xeca-1702238794916"></a><a name="xgvz-1699829941205"></a>**善用UML图 统一建模语言 （类图、方法调用时序图）**

<a name="u4qd-1699827590539"></a>**=== 重构必备快捷键===**

<a name="7jgm-1699827592479"></a>**Alt + Delete Safe Detele(安全删除，可用在方法上进行快速删除)**

<a name="zbnc-1699827592481"></a>**Shift +F6重命名-**

<a name="lcsh-1699827592483"></a>**F5/F6复制/移动元素**

<a name="svos-1699827592485"></a>**Ctrl + Alt +M抽取方法 Extract Method**

<a name="i62k-1699827592487"></a>**Ctrl + Alt+ C抽取常量**

<a name="3lvw-1699827592489"></a>**Ctrl +Alt+ F抽取字段**

<a name="8vae-1699827592491"></a>**Ctrl + Alt+P抽取参数**

<a name="0hnv-1699827592493"></a>**Ctrl + Alt+ V抽取变量**

<a name="ljc1-1699827592495"></a>**Ctrl + Alt+Shift +P抽取函数参数**

<a name="rltn-1699827592497"></a>**Ctrl + Alt+Nlnline(转换为内联、方法链形式的调用，抽取方法的反操作)**

<a name="8n32-1699827592499"></a>**Ctrl + F6Change Signature(修改方法、类的签名，含参数、返回值类型等)**


<a name="damq-1701954397345"></a><a name="deds-1701954398514"></a><a name="2yjy-1701954398769"></a>**Spring源码**

<a name="yskl-1701954404974"></a>**AOP**

<a name="ol57-1701954646926"></a>**.基本概念(面相切面)**

什么是AOP

1\.面向切面编程（方面)﹐剧用AOP可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，

同时提高了开发的效率。

2\.通俗描述:不通过修改源代码方式，在主千功能里面添加新功能

<a name="iaar-1701959528284"></a>3.使用登录例子说明AOP

<a name="5vn0-1701958435935"></a>**.底层原理(JDK动态代理 CGLIB动态代 理)**

<a name="p22c-1702323312832"></a>**1.JDK动态代理 -接口**

<a name="fl6z-1702323317995"></a>**2.CGLIB动态代理 -抽象类、类**

1、AOP底层使用动态代理(1）有两种情况动态代理  -接口

.第一种有接口情况，使用JDK动态代理           

`    `创建接口实现类代理对象，增强类的方法  //Interface i = new 接口实现类1 -多态

.第二种没有接口情况,使用CGLIB动态代理     -抽象类、类

`    `创建子类(super())的代理对象,增强类的方法

GPT anwser:

Spring AOP 使用动态代理机制来实现横切关注点的注入。对于每个被代理的 bean，Spring 在运行时创建一个代理对象，该代理对象包含了横切逻辑。

<a name="2oyz-1702063531917"></a>当客户端调用被代理对象的方法时，横切逻辑被执行，实现了横切关注点的注入。

<a name="t5yl-1701959474530"></a>**.底层原理(JDK动态代理实现)**

<a name="8jra-1702323371005"></a>**1.动态代理构建代理对象**

<a name="uiso-1702323377901"></a>**2.使用动态代理对象**

UserDao UserDaoImpl

1\.动态代理构建代理对象

UserDaoProxy implements InvacationHandle

-obj:Object //被代理对象 

+UserDaoProxy(Object obj)

`    `this.obj=obj;

+invoke(Object proxy,Method method, Object[] args):Object{ //代理对象

`  `sout("方法前");

`  `Object res = method.invoke(obj, args);

`  `sout("方法后");

`  `return res;

}

2\.使用动态代理对象

匿名内部类 new Proxy(xxxxx)

or 

userDao dao = (UserDao)Proxy.newProxyInstance(JDKProxy.class.getClassLoader(), interfaces, new UserDaoProxy(userDaoimpl));

dao.add(user);

<a name="8spm-1702145803155"></a>-----成熟的框架/复杂编程必用反射(通过反射获取Constructor、Method、Field，构造器，方法，域/成员变量)

<a name="ry4r-1702154401445"></a>**.AOP操作术语(连接点.切入点.通知/增强.切面)**

1、连接点

类里面哪些方法可以被增强,这些方法称为连接点

2、切入点

实际被真正增强的方法,称为切入点

3、Advice通知（增强)

(1）实际增强的逻辑部分称为通知（增强)

(2）通知有多钟类型

\*前置通知 before

\*后置通知  after

\*环绕通知  around

\*异常通知

\*最终通知 afterReturing finally

4\.切面-是动作

<a name="okih-1702151137671"></a>(1）把通知应用到切入点过程

<a name="7pzc-1701959416099"></a>**.AOP操作-AspectJ注解1**

.AOP操作-准备工作 -引用AspectJ

User{

`    `add(){

`        `sout("add")    

`    `};

}

@Aspect

@Component

UserProxy{

`    `@Before(value="execution(xxx.Usre.add)")

`    `sout("before")



`    `@Around(xxx.Usre.add)

`    `sout("Around之前")

`    `//继续执行中间注入的代码

`    `proceedingJoinPoint.proceed();

`    `sout("Around之前")



`    `//后置通知/返回值之后通知

`    `@AfterReturning(xxx.Usre.add)

`    `sout("afterReturning")



`    `//最终通知

`    `@After(xxx.Usre.add)

`    `sout("after")



`    `//异常通知

`    `@AfterThorwing(xxx.Usre.add)

`     `sout("AfterThorwing")   

}

@Test

User user = contex.getBean();

user.add();

Around之前....

before....

add...

Around之后...

after...

afterReturing...

-----异常通知----add(10/0;)

Aroud之前...

before...

after...

<a name="akqe-1702203833044"></a>afterThorwing...

<a name="7yy9-1701959441941"></a>**.AspectJ注解2**

<a name="65vp-1702238013766"></a>**1.相同切入点抽取(@Poincat)**

@Pointcut("execution(\*  \*..\*.\*.controller..\*.\*(..))")

public void controller() {

}

<a name="spus-1702238125621"></a>@Around("controller()")

<a name="asry-1702238027465"></a>**2.有多个增强类，设置增强类优先级(@Order)**

<a name="nj0p-1702237946263"></a>@Order(1) //值越小优先级越高 -按优先级顺序执行

<a name="2l0f-1702238022847"></a>**.Aspect配置文件(xml)**

<a name="0zkr-1702238523164"></a>xml文件的配置

<a name="rft6-1701954414068"></a>**Spring事务**

<a name="snhq-1702241780386"></a>**.事务概念(数据库事务的抽象)**

<a name="wutq-1702514681562"></a>**1.对数据库事务的抽象**

<a name="6cfq-1702514708257"></a>**2.声明式事务**

<a name="xl9m-1702514717169"></a>**3.编程式事务**

<a name="wvpz-1702514725302"></a>**4.事务传播行为**

Spring事务管理是建立在数据库事务之上的一种抽象。Spring框架提供了一种声明式的事务管理方式，使得开发者能够更加方便地管理事务，

而不需要直接操作数据库事务。

关联:

1\.声明式事务:Spring的事务管理允许通过`QTransactional’注解或XML配置文件声

明式地定义事务边界，而不需要直接编写和管理底层的数据库事务。这种方式简化了事务管理的操作，并提高了可维护性。

2编程式事务:Spring 也支持编程式事务管理，开发者可以使用编程的方式在代码中直

接控制事务的开始、提交和回滚。

3\.底层数据库事务:Spring的事务管理建立在底层数据库事务之上。Spring通过与数据库的集成，

使用JDBC或者其他持久化框架(如Hibernate、MyBatis）来实现事务的管理。

区别:

1\.抽象层次:Spring事务提供了一个抽象层，屏蔽了不同数据库的差异，使得开发者可以更加方便地切换数据库系统而无需修改事务管理的代码。

这是—个高度抽象的事务管理方式，与具体的数据库无关。

2\.声明式事务:Spring的声明式事务管理允许开发者通过注解或配置文件来定义事务的边界，而不需要在代码中编写显式的事务控制语句。

这种方式降低了事务管理的复杂性，提高了代码的可读性。

3\.编程式事务:尽管Spring支持声明式事务，但也提供了编程式事务的方式。开发者可以在代码中使用编程方式控制事务，

以满足—些特殊需求或复杂场景。------JDBC & Spring.transation.support.TransactionTemplate 

比如精细化事务粒度，比如事务内加锁，导致事务未提交就释放锁，可能引起的并发问题。

@Transational

method(){

`    `lock.lock();

`    `try{

`       `operateLogDA0.insect(operateLogDO);userDA0.updateIp(userDo.getId()，ip) 

`       `sendMsg();//发送短信非事务         

`    `}

`    `finally{

`        `lock.unlock();    --如果事务未提交锁已经释放，(极端情况下)可能导致T2获取到锁，进入try   

`    `}

}

将锁放在事务外，两种改进方法 -- 保证事务提交后才释放锁，

否则大事务等待锁释放后才能提交 or 高并发时大量事务在等待锁释放(应拿到锁后才开启事务) 会导致性能下降

1)锁内抽离出子方法做事务。

2)编程式事务，减小事务粒度。 

metho(){

`  `lock.lock();

`  `try{

`     `transactionTemplate.execute((status) -> {

`        `operateLogDA0.insert(operateLogD0);userDA0. updateIp(userDo.getId().ip);I

`        `return null;}); -- 编程式事务

`        `sendMsg();//发送短信非事务 

`  `}

`     `finally{

`        `lock.unlock();    

`    `}

});

4．事务传播行为: Spring提供了更灵活的事务传播行为设置，允许在一个事务中调用另—个事务。这种方式对于多个事务之间的关系更为友好。

总的来说，Spring 事务管理是对底层数据库事务的一种高级封装，提供了更加方便和灵活的事务管理方式，

使得开发者能够更容易地处理事务相关的逻辑。

<a name="t2yp-1702243721560"></a>总的来说，Spring 事务是建立在数据库事务之上的一种事务管理机制，提供了更高层次的抽象和便捷性，使开发者更容易使用和管理事务。

<a name="gg1m-1702241805374"></a>**.事务场景引用(银行转账)**

public void accountMoney() {

`    `try {

`        `//第一步开启事务

`        `//第二步进行业务操作/ /lucy少100

`        `userDao.reduceMoney () ;



`        `//模拟异常

`        `int i = 10/0:I



`        `// mary多100

`        `userDao. addMoney () ;



`        `//第三步没有发生异常，提交事务

`        `} catch(Exception e) {

`            `//第四步出现异常，事务回滚

`        `}

<a name="yqri-1702241932680"></a>}

<a name="rna6-1702241818624"></a>**.事务管理(service层)**

1、事务添加到JaxaEE,三层结构里面Service层（业务逻辑层）

2、在 Spring进行事务管理操作

(1）有两种方式:编程式事务管理和声明式事务管理(使用) （seata?）

3、声明式事务管理

(1)基于注解方式（使用)

(2）基于xml配置文件方式

4、在Spring进行声明式事务管理，底层使用AOP原理

5、Spring事务管理API

(1）提供一个接口，代表事务管理器，这个接口针对不同的框架提供不同的实现类;

Interface  PlatformTransationManager

Class  DataSourceTransactionManager

<a name="acj4-1702244612444"></a>6.基于注解方式

<a name="zsml-1702156135978"></a>**.底层原理(TransactionInterceptor)**

1\. `@Transactiona1`注解:

°@Transactional`注解是Spring事务管理的核心注解，用于标识哪些方法应该启用事务支持。

·该注解可以应用于类级别和方法级别，提供了一系列属性，用于配置事务的传播行为、隔离级别、超时等。

·在方法上使用‘@Transactional’注解，Spring将使用AOP(面向切面编程）机制为该方法创建一个代理，以便在方法执行前后处理事务逻辑。

2\.关键类和接口:

·`TransactionInterceptor :这是事务的核心拦截器类，实现了

'MethodInterceptor`接口。在方法调用前后，该拦截器会处理事务的开始、提交、回滚等逻辑。

·'AnnotationTransactionAttributeSource':用于解析‘@Transactional'注解，并生成‘TransactionAttribute`对象。

·'TransactionAttribute`:描述事务的属性，包括传播行为、隔离级别、只读标志等。

. `TransactionAttributeSource `:定义了获取事务属性的接口, `AnnotationTransactionAttributeSource`是其一个实现。

3\.核心流程:

·当一个标记有‘@Transactional’注解的方法被调用时，Spring AOP将创建一个代理对象，其中包含了‘TransactionInterceptor'。

·在方法执行前，‘TransactionInterceptor`会根据`@Transactiona1’注解的配置获取事务属性。

·事务属性包括了传播行为、隔离级别、只读标志等，这些属性将在方法执行过程中被使用。

<a name="s2oh-1702154830663"></a>·在方法执行后，‘TransactionInterceptor`会根据方法的执行结果决定是提交还是回滚事务。

<a name="9rmz-1696756330760"></a>**.事务传播(事务的交互)**

事务的传播行为定义了在一个事务方法被另一个事务方法调用时，它们之间事务是如何进行交互的。Spring提供了多种事务传播行为，

可以通过‘@Transactional'注解的'propagation`属性进行配置。以下是常见的事务传播行为:

1\.`REQUIRED`(默认):

·如果当前存在事务，则加入该事务;如果当前没有事务，则创建一个新的事务。·这是最常见的传播行为，适用于大多数情况。

@Transactional(propagation = Propagation.REQUIRED)

public void methodWithTransaction() {

`    `// 事务逻辑

}

2\."SUPPORTS :

·如果当前存在事务，则加入该事务;如果当前没有事务，则以非事务方式执行。

·适用于不需要强制事务的场景。-支持但不required强制

3\.“MANDATORY`:

·如果当前存在事务，则加入该事务;如果当前没有事务，则抛出异常。

4\."REQUIRES\_NEW"：

.无论当前是否存在事务，都会创建一个新的事务。如果存在事务，则挂起该事务，执行完毕后恢复原事务。-互不影响

这些传播行为提供了很大的灵活性，可以根据业务需求选择适当的事务传播行为。要注意的是，传播行为的选择可能会影响事务的隔离级别、

<a name="2li4-1702156191751"></a>性能以及对数据库的锁定行为。

<a name="xcrx-1702156171784"></a>**.事务隔离级别(同mysql)**

ioslation:事务隔离级别

1\.事务有特性成为隔离性，多事务操作之间不会产生影响。不考虑隔离性产生很多问题。

2\.有三个读问题:脏读、不可重复读、幻读/虚读

脏读:一个未提交事务读取到另一个未提交事务的数据(脏页？) -未提交可回滚

不可重复读:一个未提交事务读取到另一提交事务修改数据

幻读/虚读

3\.隔离级别

读未提交 读已提交() 可重复读 串行化

Spring的事务隔离级别与数据库事务隔离级别直接相关，Spring提供了一种抽象，使得开发者可以在声明式事务中设置所需的隔离级别。

然而，Spring的事务隔离级别是建立在数据库事务隔离级别之上的，它会映射到底层数据库系统支持的具体隔离级别。

Spring提供的事务隔离级别与数据库隔离级别的映射关系如下:

1\. DEFAULT:使用底层数据库系统的默认隔离级别。通常，数据库系统的默认隔离级别是READ COMMITTED。

2\. READ\_UNCOMMITTED:对应数据库的READ UNCOMMITTED隔离级别。允许事务读取其他事务未提交的数据。

3\. READ\_COMMITTED:对应数据库的READ COMMITTED隔离级别。确保一个事务只能读取已经提交的数据，避免脏读。

4\. REPEATABLE\_READ:对应数据库的REPEATABLE READ隔离级别。确保一个事务在执行期间多次读取相同的行时，会看到相同的数据。

避免脏读和不可重复读。

应用场景：在做统计和批量处理时不希望看到其他事务对同一数据的更新，保持读取一致性。

可重复读(Repeatable Read）是数据库事务的一种隔离级别，它确保在事务执行期间读取的数据集合保持一致，

即使在事务期间有其他事务对相同的数据进行了更新。

可重复读隔离级别的应用场景通常涉及到需要保持读取数据一致性的业务场景，尤其是在读取数据过程中，不希望看到其他事务对同一数据的更新。

以下是一些可重复读隔离级别的典型应用场景:

1)报表生成:在生成报表或统计数据的过程中，希望确保读取的数据在整个事务期间保持一致，避免因其他事务对数据的更新导致报表数据的不一致性。

2)批量处理:对大量数据进行批量处理的场景，例如数据迁移、数据清理等。在事务内执行批量处理操作时，希望读取的数据集合在整个事务期间保持一致。

3)账单生成:在生成账单或执行财务结算操作时，需要确保读取的账单数据在整个事务期间保持一致，以避免在生成账单时看到其他事务对账单数据的更新。

4)快照读取:需要对某个时间点的数据进行快照读取的场景。可重复读隔离级别可以确保在事务开始时读取的数据快照在整个事务期间保持不变，

即使其他事务对相同的数据进行了更新。

5)避免不可重复读:在一些业务场景中，要求同一事务内多次读取同一数据时，这些读

取的结果应该一致，不应受到其他事务的影响。可重复读隔离级别可以避免不可重复读的问题。

5\.SERIALIZABLE:对应数据库的SERIALIZABLE隔离级别。最高的隔离级别，确保事务的串行执行，避免脏读、不可重复读和幻读。

JDBC 设置spring事务隔离级别;

<a name="ncuc-1702291924859"></a>Connection void setTransactionIsolation(int level) throws SQLException;

<a name="u2jh-1702295830145"></a><a name="nj45-1702517125369"></a>**.事务参数**

<a name="agn5-1702323504347"></a>**1.timeout:超时时间**

<a name="6xui-1702323546562"></a>**2.readOnly:是否只读**

<a name="nnjk-1702323572146"></a>**3.rollbackfor:回滚;**

<a name="jbnx-1702323577652"></a>**4.noRollbackor:不回滚;**

1\.timeout:超时时间

(1）事务需要在一定时间内进行提交，如果不提交进行回滚·

(2)默认值是-1，设置时间以秒单位进行计算

2\.readOnly:是否只读

(1)读:查询操作，写:添加修改删除操作√

(2) readOnly默认值 false，表示可以查询，可以添加修改删除操作v

(3)设置readOnly值是true，设置成true之后，只能查询s

3\.rollbackfor:回滚;

(1）设置出现哪些异常进行事务回滚

4\.noRollbackor:不回滚;

（1）设置出现哪些异常不进行事务回滚,

====基于XML配置事务=====略

完全注解声明式事务管理

@EnableTransation

@Bean

<a name="yo2j-1702295847464"></a>TransationMagger()

<a name="ges0-1702295839157"></a>**.事务失效**

<a name="oz7x-1702323587855"></a>**1.自动提交:事务执行SQL,异常后自动提交**

<a name="xh3y-1702323627701"></a>**2. try-catch捕获异常:消费掉异常**

<a name="uzqi-1702323653445"></a>**3.不受检查异常:非RuntimeException及子类**

<a name="cxmb-1702323660680"></a>**4. Propagation属性设置错误:事务交互嵌套事务中导致事务失效**

<a name="0a5i-1702323666422"></a>**5.并发问题:死锁**

<a name="zepp-1702323671358"></a>**6.错误选择数据库隔离级别问题:READ\_UNCOMMITTED**

<a name="m69p-1702323677953"></a>**7.分布式事务问题:**

<a name="etkm-1702323684344"></a>**8.长事务:**

1\.自动提交:

·如果在事务中执行的SQL语句之后发生异常，而事务管理器没有捕获到异常并回滚事务，可能导致事务失效。这通常与数据库连接的自动提交属性有关。

2\. try-catch捕获异常:

·在事务中捕获了异常并在catch块中没有回滚事务，导致事务未能正确回滚。

try {

`    `// 事务逻辑

} catch (Exception e) {

`    `// 异常处理，未回滚事务

}

3\.不受检查异常:

·如果在事务中抛出了非受检查异常(`RuntimeException'或其子类)，默认情况下Spring会回滚事务。但如果异常被捕获并处理，事务就可能失效。

4\. Propagation属性设置错误:

·错误地设置了事务传播属性，可能导致事务失效。例如，设置了'Propagation.REQUIRES\_NEW`可能在嵌套事务中导致事务失效。

5\.并发问题:

·在多线程或并发环境中，可能发生数据竞争或死锁等问题，导致事务无法正确完成。

6．数据库隔离级别问题:

·选择错误的数据库隔离级别，例如设置为`READ\_UNCOMMITTED`，可能导致事务隔离性失效。

7\.分布式事务问题:

·在分布式环境中，分布式事务的实现需要考虑全局事务的一致性。如果分布式事务管理不当，可能导致整个事务失效。

8\.长事务:

·长事务可能导致数据库锁定时间过长，影响系统性能，并可能导致其他事务失效。

在使用事务时，确保正确配置事务管理器，处理异常时正确回滚事务，并正确选择事务传播属性是保障事务有效性的关键。

<a name="ucnf-1702156484569"></a>同时，仔细考虑业务逻辑和事务边界，以及在分布式环境下的一致性问题。

<a name="peq9-1702156163512"></a>**注解**

注解的应用场景:（可看@Transactional）

1\.代码分析工具:注解可以提供额外的代码信息，用于代码分析工具进行静态分析。

2\.编译时处理:注解处理器在编译时可以生成额外的代码，用于完成一些自动化的任务。

3\.配置文件生成:注解可以用于生成配置文件，例如在Web开发中生成XML配置文件。

总的来说，注解为Java提供了一种方便、灵活的元数据机制，通过注解，程序员可以在代码中嵌入更多的信息，提高代码的可读性和可维护性。

<a name="8i3t-1702155047024"></a>在一些框架和库中，注解也被广泛用于实现各种功能。

<a name="zpsm-1702155028191"></a>**循环依赖**

在 Spring 中，循环依赖是指两个或多个 Bean 互相依赖，形成一个循环依赖关系。这种情况可能导致 Spring 在实例化这些 Bean 时出现问题。

Spring 通过使用三级缓存来解决循环依赖的问题。

以下是Spring如何处理循环依赖的简要解释:

1\.首次调用:

·当容器第一次发现循环依赖时，它会实例化正在处理的Bean，并将其放入早期引用缓存(early reference cache)。这个缓存是一级缓存，用于存放正在创建中的Bean。

2．创建代理:

·如果发现循环依赖，Spring 会创建一个代理对象，代理对象会覆盖原始Bean的实例。这个代理对象会被放入早期引用缓存。

3\.属性注入:

Spring 完成Bean的实例化后，会将这个Bean放入普通缓存，并进行属性注入。4．初始化和后处理:

·之后，Spring 会按正常的初始化和后处理阶段继续工作。

这种方式能够解决循环依赖的问题，但需要注意的是，Spring 要求被循环依赖的Bean至少有一个是prototype(原型）)作用域的。这是因为单例(singleton)作用域的 Bean在容器初始化时就创建好了，无法在运行时创建代理对象来解决循环依赖。

@Component

public class A {

`    `private B b;

`    `@Autowired

`    `public A(B b) {

`        `this.b = b;

`    `}

}

@Component

public class B {

`    `private A a;

`    `@Autowired

`    `public B(A a) {

`        `this.a = a;

`    `}

}

在这个示例中，A和B互相依赖。Spring 会正确处理这种情况，确保A和B都被正确实例化。但要注意，如果A或B是单例作用域的话，

<a name="qycv-1702236210959"></a>就需要注意循环依赖可能导致的问题。

<a name="gvfv-1702236185333"></a>**设计模式-重构**

<a name="w0cs-1696756330761"></a>**通用原则**

<a name="aj9d-1699828474925"></a>**-代码 开放/封闭 原则，**

` `由Bertrand Meyer提出。

其背后原理是，代码对于扩展应该是开放的，对于修改应该是封闭的。  4. 将重复代码封装，复用。

好的设计，无需对代码太多的修改就可以添加新的特性。修改场景下，许多情况下只需要对极少数的方法稍加修改即可，

还有一些情况下只需要派生一个新的类即可。派生之后很重要的一点是要记得消除重复（看差异式编程，通过派生来添加新特性以及通过重构整合它们）

<a name="atl3-1702062005179"></a>消除重复后，代码自然而然的往 开放/封闭 原则靠拢了。

<a name="6bga-1649502279787"></a>**- 多用组合，少用继承**

<a name="ub5i-1649502231177"></a>**-依赖倒置原则-面向接口编程**

<a name="oenx-1702062032802"></a>面向抽象接口编程，不要依赖具体实现，减少类与类的耦合性，提高系统的可读性和可维护性

<a name="on9f-1649502485850"></a>**-依赖抽象，不要依赖具体类**

Throwable    class

`    `Exception    class

`        `RuntimeException    class

`            `AbstractAppException  abstract class  --声明APP异常抽象类 方便@ExceptionHandler(AbstractAppException.class)

`                `BadRequestException  class

<a name="wesp-1702325244665"></a>                ResourceException    class

<a name="dl5h-1702325051758"></a>**-独立需要变化和不需要变化的代码**

<a name="6orr-1702325088901"></a>**-交互对象之间要松耦合设计**

<a name="van1-1702325113068"></a>**-一个类应该只有一个引起变化的原因(单继承？)**

<a name="vmrt-1702325157809"></a>**-最少知识原则，只和密友谈话**

<a name="fgkj-1702325179787"></a>**-别调用我们，我们会调用/通知你**

<a name="uqel-1702325054883"></a><a name="dout-1702325047416"></a>**工厂模式(产品接口，工厂接口)**

<a name="cpml-1702332761576"></a>**客户端代码可以通过选择不同的工厂来创建不同的产品**

<a name="qfre-1702333590011"></a>**1.产品接口  具体产品1 具体产品2**

<a name="lx6u-1702333615242"></a>**2.工厂接口  具体工厂1-构造产品1  具体工厂2-构造产品2** 

<a name="mhgn-1702333854385"></a>**3. 选择不同的工厂创建不同的产品**

定义一个用于创建对象的接口，让子类决定实例化哪一个类。工厂 方法使一个类的实例化延迟到其子类。

面相接口编程，而不是具体的子类，java多态的体现。

在这个示例中，"Product`是产品的接口，`ConcreteProductA`和"ConcreteProductB·是具体的产品类。"Factory`是工厂的接

口，"ConcreteFactoryA`'和ConcreteFactoryB’是具体的工厂类。客户端代码可以通过选择不同的工厂来创建不同的产品，

从而实现了对象的创建和使用的解耦。这是一个简单的工厂模式示例，实际应用中可能会更加复杂。

// 产品接口

interface Product {

`    `void create();

}

// 具体产品A

class ConcreteProductA implements Product {

`    `@Override

`    `public void create() {

`        `System.out.println("Product A created");

`    `}

}

// 具体产品B

class ConcreteProductB implements Product {

`    `@Override

`    `public void create() {

`        `System.out.println("Product B created");

`    `}

}

// 工厂接口

interface Factory {

`    `Product createProduct();

}

// 具体工厂A，用于创建ProductA

class ConcreteFactoryA implements Factory {

`    `@Override

`    `public Product createProduct() {

`        `return new ConcreteProductA();

`    `}

}

// 具体工厂B，用于创建ProductB

class ConcreteFactoryB implements Factory {

`    `@Override

`    `public Product createProduct() {

`        `return new ConcreteProductB();

`    `}

}

// 客户端代码

public class FactoryPatternExample {

`    `public static void main(String[] args) {

`        `// 使用工厂A创建ProductA

`        `Factory factoryA = new ConcreteFactoryA();

`        `Product productA = factoryA.createProduct();

`        `productA.create();

`        `// 使用工厂B创建ProductB

`        `Factory factoryB = new ConcreteFactoryB();

`        `Product productB = factoryB.createProduct();

`        `productB.create();

`    `}

<a name="u7pc-1702063332726"></a>}

<a name="jm2n-1696756330762"></a>**单例模式**

<a name="vnxl-1702337056413"></a>1.

确保某一个类只有一个实例，而且自行实例化并向整个系统提供这 个实例。

<a name="el4f-1702063342747"></a>分布式中还是单例模式吗？===类似分布式并发锁问题，通过分布式锁机制or数据库锁保证只生成一个实例，存储在分布式缓存中或数据库中

<a name="hzzm-1696756330763"></a>**装饰器模式(组件接口，抽象装饰器实现组件接口)**

<a name="jf1v-1678827490022"></a>**静态代理加一层抽象类（duck）就是装饰器模式了(fly duck, roket duck)。**

<a name="oash-1678827451389"></a>动态地给一个对象添加一些额外的职责。就增加功能来说，装饰 器模式相比生成子类更为灵活 。通常只有一个。

<a name="vkm1-1677978057446"></a>定义一个**抽象类实现接口**，组合接口(**持有接口对象，构造器注入**)，装饰器类**继承**抽象接口(**构造器引用super()**)，重写方法增强操作或增加新方法。

<a name="ooet-1677977953185"></a>装饰器模式适用于以下情况：

<a name="pdin-1677977953191"></a>当我们想要在不改变原有类结构的情况下，动态地给一个对象增加一些额外的功能或职责时，可以使用装饰器模式来实现[**3**](https://developer.aliyun.com/article/864585)

<a name="kmh9-1677978057815"></a>当我们想要通过**组合不同的装饰类来得到多种功能组合**时，可以使用装饰器模式来实现

<a name="8nqr-1702334948103"></a>**客户端代码可以选择性地使用装饰器来包装具体组件**

<a name="vc2u-1702333931030"></a>**1.组件接口，Concrete具体组件1  具体组件2**

<a name="rmxw-1702334202292"></a>**2.抽象装饰器实现组件接口  具体装饰器1  具体装饰器2**

<a name="jbhr-1702334336845"></a>**3.使用具体装饰器包装具体组件  Component decoratedComponentA = new ConcreteDecoratorA(componentC);**

在这个示例中，"Component’是组件的接口，`ConcreteComponent'是具体的组件类。'Decorator`是装饰器的抽象类，继承自`Component'，

并包含一个成员变量'component'，代表被装饰的组件。`ConcreteDecoratorA`和'ConcreteDecoratorB"是具体的装饰器类，

它们扩展了‘Decorator`并添加了额外的操作。

客户端代码可以选择性地使用装饰器来包装具体组件，从而实现不同的组合效果。这种方式使得在不修改现有代码的情况下，可以灵活地扩展对象的功能。

// 组件接口

interface Component {

`    `void operation();

}

// 具体组件，实现了组件接口的基本操作

class ConcreteComponent implements Component {

`    `@Override

`    `public void operation() {

`        `System.out.println("ConcreteComponent operation");

`    `}

}

// 装饰器抽象类，继承自组件接口

abstract class Decorator implements Component {

`    `protected Component component;

`    `public Decorator(Component component) {

`        `this.component = component;

`    `}

`    `@Override

`    `public void operation() {

`        `component.operation();

`    `}

}

// 具体装饰器A，扩展了Decorator，添加了额外的操作

class ConcreteDecoratorA extends Decorator {

`    `public ConcreteDecoratorA(Component component) {

`        `super(component);

`    `}

`    `@Override

`    `public void operation() {

`        `super.operation();

`        `addAdditionalOperation();

`    `}

`    `private void addAdditionalOperation() {

`        `System.out.println("ConcreteDecoratorA additional operation");

`    `}

}

// 具体装饰器B，扩展了Decorator，添加了另外的额外操作

class ConcreteDecoratorB extends Decorator {

`    `public ConcreteDecoratorB(Component component) {

`        `super(component);

`    `}

`    `@Override

`    `public void operation() {

`        `super.operation();

`        `addAnotherAdditionalOperation();

`    `}

`    `private void addAnotherAdditionalOperation() {

`        `System.out.println("ConcreteDecoratorB another additional operation");

`    `}

}

// 客户端代码

public class DecoratorPatternExample {

`    `public static void main(String[] args) {

`        `// 创建具体组件

`        `Component component = new ConcreteComponent();

`        `// 使用装饰器A包装组件

`        `Component decoratedComponentA = new ConcreteDecoratorA(component);

`        `decoratedComponentA.operation();

`        `System.out.println();

`        `// 使用装饰器B包装组件

`        `Component decoratedComponentB = new ConcreteDecoratorB(component);

`        `decoratedComponentB.operation();

`    `}

<a name="fepo-1702333325615"></a>}

<a name="ph56-1696756330764"></a>**装饰器和代理的区别：**

<a name="psj7-1677978919986"></a>**1.装饰器模式关注于在一个对象上动态地添加方法，而代理模式关注于控制对对象的访问。**

<a name="vdgu-1677978921450"></a>**2.装饰器模式是为了增强原有对象的功能，而代理模式是为了施加控制或者提供额外的服务。**

<a name="ecno-1677978921452"></a>**3.装饰器模式中，装饰类和目标类是解耦的，装饰对象不感知目标对象的存在，由调用方控制对目标对象的引用。而代理模式中，代理类和目标类是耦合的，代理对象控制对目标对象的引用。**

<a name="vany-1677978921454"></a>**4.装饰器模式通常只有一个装饰类，而代理模式可以有多个代理类。**

<a name="k4d4-1702335689176"></a>**5.代理类注入的是具体目标类，强耦合，多个目标类需要写多个代理类-静态代理；动态代理动态生成代理对象，无需为每个类都手动编写代理类）**

<a name="rgbn-1702336021986"></a>**6.抽象装饰器注入的是组件接口，调用方控制对目标组件对象们的引用，灵活组合**

<a name="cocv-1702335104756"></a>**代理模式(主题接口，代理类实现主题接口)**

<a name="zmqj-1702335858368"></a>**客户端通过代理类对方法进行增强**

<a name="ickc-1702335156454"></a>**1.主题接口，具体主题**

<a name="he1l-1702335163013"></a>**2.代理类实现主题接口，并注入具体主题**

<a name="nipw-1702335663657"></a>**3. 对具体主题进行增强**

<a name="wtvy-1702336278237"></a>**动态代理，动态生成代理对象**

<a name="3hi4-1702336292130"></a>**1.代理类实现InvocationHandle接口**

<a name="8j5x-1702336513852"></a>**2. 注入为Object类，利用反射执行Object方法，返回代理对象**

<a name="l9oy-1702336337485"></a>**3.对具体主题进行增强**

<a name="kh2k-1702336284590"></a><a name="eqbx-1678827469637"></a>**（**被代理类/原始类实现接口），**代理类实现上相比装饰器类清楚一丢丢,少一层抽象类**

<a name="xrlu-1677978633053"></a>静态代理：代理类实现具体某个接口，组合接口(**持有接口对象，构造器注入**)，重写方法对被代理类进行增强。

<a name="rpgp-1677978642342"></a>动态代理：代理类实现反射类接口，通过反射动态生成代理类。对代理类进行增强。组合Object(持有Object对象，构造器注入)

<a name="fz6y-1702334811416"></a>静态: UserDaoProxy implements UserDao -usrDaoImpl:UserDaoImpl

<a name="pwme-1702145166526"></a>动态：UserDaoProxy implements InvocationHandle -Object obj(被代理对象) +invoke(Object ):Object(代理对象)  

<a name="acmn-1677977988299"></a>代理模式适用于以下情况：

<a name="7rfw-1677977953174"></a>当我们想要隐藏某个类时，可以为其提供代理类[**2**](https://www.cnblogs.com/V1haoge/p/6525527.html)

<a name="tpnk-1677977953178"></a>当一个类需要对不同的调用者提供不同的调用权限时，可以使用代理类来实现

<a name="kdh0-1677977953183"></a>当我们想要在真实主题执行之前或之后做一些预处理或后续处理时，可以使用代理类来实现

<a name="iqzu-1678033126970"></a>动态代理和静态代理都是设计模式中的代理模式，它们的主要目的是在不改变原始类的情况下，为其增加额外的功能。但是它们的实现方式有所不同，具体如下：

<a name="o2u1-1702144789223"></a><a name="mrds-1678033153900"></a>实现方式：静态代理(也称编译时期代理)需要手动编写代理类，而动态代理不需要编写代理类，可以在运行时动态地生成代理类。

<a name="dh2g-1678033153904"></a>对象类型：静态代理和动态代理都需要代理类和原始类实现相同的接口，但**静态代理代理的是一个具体的类，而动态代理可以代理任何实现了接口的类。**

<a name="smcq-1678033153908"></a>生命周期：静态代理的代理对象在编译时就已经确定，不能动态改变，而动态代理的代理对象可以在运行时动态生成，可以根据需要动态改变。

<a name="t69s-1678033153912"></a>性能：静态代理在**编译时就已经生成了代理类(class文件）**，因此效率较高，但需要手动编写代理类(指定实例)；**动态代理在运行时动态生成代理类(利用反射机制生成的类也称动态类，**代理类的字节码是由虚拟机在运行时根据需要动态生成的，通常存储在内存中，而不是以 class 文件的形式存在磁盘上。**)，因此效率较低，但可以根据需要动态生成代理对象(反射)**。

<a name="abkp-1678033153914"></a><a name="6wve-1678033153916"></a>综上所述，静态代理和动态代理都可以实现代理模式的功能，但是它们的实现方式和应用场景有所不同。静态代理适用于代理类和原始类的关系比较固定的情况下，而动态代理适用于代理类和原始类的关系比较灵活的情况下。此外，动态代理还可以用于实现AOP（面向切面编程）等高级功能。

在这个示例中,"Subject'是一个接口，`RealSubject`是具体的实现类。"Proxy`是代理类，实现了"Subject`接口，

并在其中持有一个真实对象`RealSubject’的引用。"Proxy`类通过实现‘Subject'接口，实现了对‘RealSubject'的代理。

在客户端代码中，创建了一个真实对象‘RealSubject'和一个代理对象`Proxy`，然后通过代理对象调用方法。在代理对象的方法中，

可以添加额外的逻辑，例如在被代理对象的方法调用前后输出日志。

静态代理的缺点是如果有多个类需要代理，就需要为每个类编写一个代理类，代码重复较多。

此外，如果接口发生变化，代理类和被代理类都需要进行修改。

// 接口

interface Subject {

`    `void request();

}

// 具体实现类

class RealSubject implements Subject {

`    `@Override

`    `public void request() {

`        `System.out.println("RealSubject handles request");

`    `}

}

// 代理类

class Proxy implements Subject {

`    `private RealSubject realSubject;

`    `public Proxy(RealSubject realSubject) {

`        `this.realSubject = realSubject;

`    `}

`    `@Override

`    `public void request() {

`        `// 可以在被代理对象的方法调用前后添加额外的逻辑

`        `System.out.println("Proxy handles request before");

`        `realSubject.request();

`        `System.out.println("Proxy handles request after");

`    `}

}

// 客户端代码

public class StaticProxyExample {

`    `public static void main(String[] args) {

`        `// 创建真实对象

`        `RealSubject realSubject = new RealSubject();

`        `// 创建代理对象并将真实对象传递给代理对象

`        `Proxy proxy = new Proxy(realSubject);

`        `// 通过代理对象调用方法

`        `proxy.request();

`    `}

<a name="qwzz-1702335790211"></a>}

<a name="o71j-1702336501373"></a>在这个示例中，‘Subject`是接口，‘Rea1Subject`是真实实现类。

"DynamicProxyHandler’是实现了‘InvocationHandler`接口的代理类，它包含一个成员变量'target'，代表被代理的真实对象。

在‘invoke'方法中，可以在被代理对象的方法调用前后添加额外的逻辑。

在客户端代码中，通过调用‘Proxy.newProxyInstance'方法动态创建代理对象。

这个方法接收三个参数:类加载器、接口数组和"InvocationHandler'实现类。通过这个代理对象调用方法时，

实际上会调用‘DynamicProxyHandler'中的‘invoke'方法。

动态代理的优势在于可以为多个类动态生成代理，无需为每个类都手动编写代理类，减少了代码的重复性。

import java.lang.reflect.InvocationHandler;

import java.lang.reflect.Method;

import java.lang.reflect.Proxy;

// 接口

interface Subject {

`    `void request();

}

// 真实实现类

class RealSubject implements Subject {

`    `@Override

`    `public void request() {

`        `System.out.println("RealSubject handles request");

`    `}

}

// InvocationHandler 实现类

class DynamicProxyHandler implements InvocationHandler {

`    `private Object target;

`    `public DynamicProxyHandler(Object target) {

`        `this.target = target;

`    `}

`    `@Override

`    `public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {

`        `// 在被代理对象的方法调用前后添加额外的逻辑

`        `System.out.println("DynamicProxy handles request before");

`        `Object result = method.invoke(target, args);

`        `System.out.println("DynamicProxy handles request after");

`        `return result;

`    `}

}

// 客户端代码

public class DynamicProxyExample {

`    `public static void main(String[] args) {

`        `// 创建真实对象

`        `RealSubject realSubject = new RealSubject();

`        `// 创建动态代理对象

`        `Subject proxy = (Subject) Proxy.newProxyInstance(

`                `Subject.class.getClassLoader(),

`                `new Class[]{Subject.class},

`                `new DynamicProxyHandler(realSubject)

`        `);

`        `// 通过代理对象调用方法

`        `proxy.request();

`    `}

<a name="te8v-1702336501371"></a>}

<a name="srgw-1696756330765"></a>**适配器模式：**

<a name="eeir-1703089634191"></a>**1.220V接口，110V接口**

<a name="pvyr-1703089725206"></a>**2.适配器类实现220V接口，并注入110V接口**

<a name="1ovh-1703090953107"></a>**3.将220V转换为110V接口**

<a name="reyu-1703091219847"></a>新增一个适配接口/类保持与原接口方法相同，干代理模式的活

新增一个适配接口保持与原接口方法相同，干代理模式的活

适配器模式主要解决接口不兼容的问题，使得原本不兼容的类能够协同工作；而代理模式主要解决控制对对象的访问的问题，

引入代理类来实现对原始类的控制。虽然它们有相似的结构，但目的和应用场景不同

适配器模式的核心思想是将一个类的接口转换成客户希望的另外一个接口。适配器模式可以解决接口不兼容的问题，

让原本由于接口不匹配而无法在一起工作的类能够协同工作。

新表、老表

1\.定义适配器接口，与原接口具有相同的方法名称和方法签名

<a name="ecrw-1703091192383"></a>2.实现适配器类，并引用原来的DAO接口和新DAO接口

<a name="iazq-1703091176863"></a><a name="y76p-1696756330766"></a>**策略模式:(常用替换if else）**

<a name="medy-1703092035603"></a>**1.环境类（contex）:注入策略接口， excute执行逻辑** 

<a name="idgz-1678386529147"></a>**1.策略接口**

<a name="1imw-1678386551525"></a>**2.具体策略：策略接口多种实现类**

<a name="tiwh-1678386674027"></a>优点：提高代码可读性、符合开放封闭原则、实现算法和调用者之间的解耦，提高代码复用性

<a name="hxzr-1678386833573"></a>缺点：需要创建多个策略实现类和一个环境类、客户端需要知道所有策略对应关系（HashMap映射策略），增加了客户端复杂度

// 策略接口

interface PaymentStrategy {

`    `void pay(int amount);

}

// 具体策略：支付宝支付

class AlipayStrategy implements PaymentStrategy {

`    `@Override

`    `public void pay(int amount) {

`        `System.out.println("Paid " + amount + " using Alipay");

`    `}

}

// 具体策略：微信支付

class WeChatPayStrategy implements PaymentStrategy {

`    `@Override

`    `public void pay(int amount) {

`        `System.out.println("Paid " + amount + " using WeChat Pay");

`    `}

}

// 环境类

class PaymentContext {

`    `private PaymentStrategy paymentStrategy;

`    `public PaymentContext(PaymentStrategy paymentStrategy) {

`        `this.paymentStrategy = paymentStrategy;

`    `}

`    `public void performPayment(int amount) {

`        `paymentStrategy.pay(amount);

`    `}

}

// 客户端代码

public class StrategyPatternExample {

`    `public static void main(String[] args) {

`        `// 创建支付策略

`        `PaymentStrategy alipay = new AlipayStrategy();

`        `PaymentStrategy weChatPay = new WeChatPayStrategy();

`        `// 创建支付环境，并设置支付策略

`        `PaymentContext paymentContext = new PaymentContext(alipay);

`        `// 执行支付

`        `paymentContext.performPayment(100);

`        `// 切换支付策略

`        `paymentContext = new PaymentContext(weChatPay);

`        `// 执行支付

`        `paymentContext.performPayment(150);

`    `}

<a name="nfi7-1703092157680"></a>}

<a name="5pye-1703091114266"></a><a name="xa1i-1699829834311"></a>**AOP用到的设计模式**

<a name="2rlp-1699829827091"></a>**-代理模式：**

<a name="ku11-1699829827425"></a> Spring AOP基于代理模式实现了面向切面编程。它使用代理对象包装目标对象，在方法调用时可以在目标方法的前后织入横切关注点。

<a name="ujdc-1699829827427"></a>**-观察者模式：**

<a name="vtll-1699829827429"></a> Spring AOP中的通知（Advice）就类似于观察者模式中的观察者。它们可以观察切入点的状态并在需要时执行相应的操作。

<a name="toz8-1701952321001"></a>**Mybatis动态代理源码解析**

MyBatis 使用动态代理的源码主要集中在 org.apache.ibatis.binding.MapperProxyFactory 和

` `org.apache.ibatis.binding.MapperProxy 类中。以下是简要的源码解析：

`    `1.MapperProxyFactory：

`        `MapperProxyFactory 是 MyBatis 中负责创建动态代理的工厂类。

`        `当 Mapper 接口被注册时，MapperProxyFactory 会为该接口创建一个代理实例。

// MyBatis 中的 MapperProxyFactory 类

public class MapperProxyFactory<T> {

`    `private final Class<T> mapperInterface;

`    `private final Map<Method, MapperMethod> methodCache = new ConcurrentHashMap<>();

`    `public MapperProxyFactory(Class<T> mapperInterface) {

`        `this.mapperInterface = mapperInterface;

`    `}

`    `public T newInstance(SqlSession sqlSession) {

`        `final MapperProxy<T> mapperProxy = new MapperProxy<>(sqlSession, mapperInterface, methodCache);

`        `return newInstance(mapperProxy);

`    `}

`    `protected T newInstance(MapperProxy<T> mapperProxy) {

`        `return (T) Proxy.newProxyInstance(mapperInterface.getClassLoader(), new Class[]{mapperInterface}, mapperProxy);

`    `}

}

`    `2.    MapperProxy：

`        `MapperProxy 是动态代理类，实现了 InvocationHandler 接口。

`        `在 invoke 方法中，它负责将代理方法的调用委托给 SqlSession 进行实际的数据库操作。

// MyBatis 中的 MapperProxy 类

public class MapperProxy<T> implements InvocationHandler, Serializable {

`    `private static final long serialVersionUID = -6424540398559729838L;

`    `private final SqlSession sqlSession;

`    `private final Class<T> mapperInterface;

`    `private final Map<Method, MapperMethod> methodCache;

`    `public MapperProxy(SqlSession sqlSession, Class<T> mapperInterface, Map<Method, MapperMethod> methodCache) {

`        `this.sqlSession = sqlSession;

`        `this.mapperInterface = mapperInterface;

`        `this.methodCache = methodCache;

`    `}

`    `@Override

`    `public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {

`        `try {

`            `// 根据方法缓存获取 MapperMethod

`            `MapperMethod mapperMethod = cachedMapperMethod(method);

`            `// 执行 SQL 操作

`            `return mapperMethod.execute(sqlSession, args);

`        `} catch (Exception e) {

`            `throw ExceptionUtil.unwrapThrowable(e);

`        `}

`    `}

`    `private MapperMethod cachedMapperMethod(Method method) {

`        `return methodCache.computeIfAbsent(method, k -> new MapperMethod(mapperInterface, method,

`         `sqlSession.getConfiguration()));

`    `}

}

在这两个类的代码中，可以看到 Proxy.newProxyInstance 方法用于创建动态代理实例，并指定了代理的接口（mapperInterface）和代理类

（MapperProxy）。在 MapperProxy 的 invoke 方法中，实现了具体的数据库操作逻辑，将方法调用委托给 SqlSession 进行执行。

<a name="ivqx-1702154366114"></a>这样，用户在调用 Mapper 接口的方法时，实际上是调用了动态代理类的 invoke 方法，而代理类则通过 SqlSession(JDBC) 执行了相应的数据库操作。

<a name="tyc5-1702154664221"></a>**编程术语**

<a name="9inw-1702516779934"></a>**脏数据**

<a name="vtbf-1702517147469"></a>**.未提交的数据: 脏读**

<a name="doto-1702517147470"></a>**.已提交的数据但未持久化: Innodb BufferPool脏页刷入磁盘**

<a name="4yp9-1702517147471"></a>**.数据冲突: 同时修改被覆盖**

<a name="4nkl-1702517147472"></a>**.数据格式错误: DB导入数据格式错误**

<a name="weer-1702517147473"></a>**.缓存不一致: DB缓存不一致**

1\.未提交的数据: 脏读

在事务尚未提交的情况下，其他事务读取到了未提交的数据，导致读到了不一致的状态。

2\.已提交的数据但未持久化: Innodb BufferPool脏页刷入磁盘

数据已经提交到数据库，但由于某种原因（例如数据库故障、网络问题等)，数据未被持久化到磁盘，可能会导致数据丢失。

3\.数据冲突: 同时修改被覆盖

多个事务同时修改相同的数据，但只有一个事务的修改会生效，导致部分事务的修改被覆盖。

4\.数据格式错误: DB导入数据格式错误

数据存储中的数据不符合预期的格式，可能是由于编程错误或数据导入错误引起的。

5\.缓存不一致: DB缓存不一致

<a name="kfpu-1702292851155"></a>在使用缓存的情况下，缓存中的数据与底层数据存储不一致，可能会导致读取到过期或者错误的数据。

<a name="7qhf-1702516793084"></a>**自旋(循环执行,不阻塞自己)**

<a name="heoy-1702516915331"></a>**.自旋锁(循环检查锁是否释放)**

<a name="wfj6-1702516920265"></a>**.自旋等待(反复检查条件是否满足)**

在计算机科学中，自旋（Spin）是一种在等待某个条件变为真时持续重复执行的行为。自旋通常是在多线程或并发编程中用于实现一种轻量级的等待机制。

相比于使用阻塞（如使用锁或信号量-线程池许可证数量，导致线程被挂起），自旋的特点是线程会一直执行一些忙等的操作，不会阻塞自己。

自旋的基本思想是，线程在等待某个条件满足时不去睡眠，而是一直循环检查条件是否满足。这样做的好处是减少了线程上下文切换的开销，

因为线程一直在执行，不需要被挂起和唤醒。但是，如果条件一直不满足，自旋可能会导致资源的浪费，因为线程一直在占用 CPU 资源。

在多线程编程中，自旋锁和自旋等待是两个常见的应用场景：

1\.自旋锁（Spin Lock）：

线程在获取锁时，如果发现锁已经被其他线程占用，它会一直循环检查锁是否被释放，而不是被挂起。一旦锁被释放，线程立即获取锁。

` `自旋锁适用于锁的持有时间非常短暂的情况。

2\.自旋等待（Spin Waiting）：

` `在一些并发算法中，线程可能需要等待某个条件满足。如果条件尚未满足，线程可能会进行自旋等待，反复检查条件是否满足。

` `这在一些特定的场景中可以减少线程阻塞的时间。



需要注意的是，自旋的效果很大程度上依赖于系统的硬件和操作系统的支持。在一些情况下，自旋可能是一种高效的等待方式，

<a name="myxx-1702516844281"></a>但在其他情况下，可能会导致性能下降。因此，使用自旋时需要根据具体的场景和硬件特性进行权衡。

<a name="mfpx-1702516831964"></a>**CAS(compare-current & swap-next)**

CAs (Compare and Swap）是一种并发算法，用于实现多线程环境下的原子操作。它是一种无锁的操作，

通常用于解决多线程并发访问共享数据时的竞态条件问题。

CAS操作包括三个步骤:

1\.比较(Compare):首先，系统会比较当前内存中的值与预期的值是否相等。

2\.交换(and Swap):如果比较的结果为真，即当前内存中的值等于预期的值，那么将内存中的值替换为新的值。

3\.返回(Compare and Swap) :返回比较的结果，指示操作是否成功。

整个CAS操作是原子性的，意味着在执行期间不会被中断，其他线程不能干扰。

在Java中,"java.util.concurrent.atomic`包提供了一系列原子类，例如

'AtomicInteger'、‘AtomicLong '、‘AtomicReference '等，它们底层使用了CAS操作。以‘AtomicInteger`为例，以下是一个简单的示例:

import java.util.concurrent.atomic.AtomicInteger;

public class AtomicExample {

`    `private static AtomicInteger counter = new AtomicInteger(0);

`    `public static void main(String[] args) {

`        `// 使用 CAS 原子操作自增

`        `int oldValue = counter.get();

`        `int newValue = oldValue + 1;

`        `while (!counter.compareAndSet(oldValue, newValue)) {   //native boolean compareAndSwapInt()

`            `// 如果 compareAndSet 返回 false，表示 CAS 失败，需要重新尝试

`            `oldValue = counter.get();

`            `newValue = oldValue + 1;

`        `}

`        `System.out.println("Incremented value: " + counter.get());

`    `}

}

CAS可以用于实现一些基本的原子操作，但也有一些限制，例如ABA问题(一个值被修改两次，但在整个过程中没有其他线程修改它)。

为了解决这些问题，Java提供了'AtomicStampedReference'和‘AtomicMarkableReference'等类，允许在CAS操作中添加额外的标记，

<a name="ywv3-1702519705452"></a>以便更安全地进行操作。

<a name="7xtw-1696756397430"></a>**《改善既有代码的设计》**

<a name="5bsg-1696756435821"></a>1.重构的第一个案例
