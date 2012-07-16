---
layout: post
title: Symfony及其版本
meta_keywords: Symfony,Symfony2,Symfony版本,如何学习Symfony,Silex
meta_description: Symfony是什么？适合我吗？我应该选择哪个版本？
categories: [kb, kb_symfony]
active_nav: kb
---

基于Symfony，程序员可以更高效地开发Web应用，这个结论，体现在以下方面：

* Symfony可以作为技术架构的基础。Symfony所采用的MVC，是经大量项目的实践，被证明可行的一套技术方案。了解或者正在学习MVC架构的Web开发人员数量很多，在他们之间，技术问题的描述更直观，任务的分工也更明确。良好的沟通，是开发效率的最大保障。
* Symfony提供了解决Web开发中常见问题的工具代码。领域和规模虽然不同，在开发Web应用的过程中，很多时候，开发者都是在解决相似的问题，因此，Symfony所提供的通用代码，可以为开发者节约很多时间，从宏观层面上来看，大量的开发人员因此可以将精力投入到更重要的事情中去：比如改进Symfony，或者为自己的公司接更多的业务。
* Symfony是一个活跃的开源项目。这意味着你的问题可以得到他人的解答，Symfony的Bug会得到处理，Symfony功能会进一步完善。
* Symfony是面向商业应用的框架，其凝结的技术经验，是开发人员宝贵的学习资料。

如果你打算学习Symfony，你首先应该了解Symfony的各个版本，及其状态。

Symfony的版本
-------------

由于国内Symfony技术资料相对陈旧、零散，大多是关于Symfony 1.x版本，所以，如果你新接触Symfony，请确保直接学习2.x版本。不过，对于熟练掌握Symfony 1.4的开发者来说，Symfony 1.4依然是提高工作效率的利器。

1.4版本的功能开发已经冻结，由于有大量的项目依然基于这个版本，所以1.4版本将来仍然会针对可能发现的严重Bug进行修正，其他方面在下表中对比：

<table class="table table-bordered">
    <tr>
        <th></td>
        <th>Symfony 1.4</th>
        <th>Symfony 2</th>
    </tr>
    <tr>
        <td>最新稳定版</td>
        <td>1.4.18</td>
        <td>2.0.16</td>
    </tr>
    <tr>
        <td>支持的PHP版本</td>
        <td>5.2.4以上</td>
        <td>5.3.2以上</td>
    </tr>
    <tr>
        <td>维护终止时间</td>
        <td>2012年11月终止功能开发</td>
        <td>未定</td>
    </tr>
    <tr>
        <td>依赖管理</td>
        <td>使用PEAR来管理插件</td>
        <td>2.0通过脚本来管理<br />
        从2.1开始使用Composer</td>
    </tr>
    <tr>
        <td>测试框架</td>
        <td>没有整合</td>
        <td>PHPUnit</td>
    </tr>
    <tr>
        <td>社区活跃度</td>
        <td>正在往2.x版本迁移</td>
        <td>活跃，GitHub上PHP项目排行第一</td>
    </tr>
</table>

<p><span class="label">提示</span> 在搜索引擎里，如果要查找关于Symfony2的资料，搜索“Symfony 2”，而不是“Symfony”。</p>

Silex
-----

Silex和Symfony同样出自法国的Sensio Labs。Symfony 2的定位是一款“全功能”的PHP框架，包含了从开发、维护/部署、测试等等大量的实用工具。Silex则是简化版的Symfony 2，只整合了Symfony2里几个最主要的组件，如HttpFoundation和DI，更适合用于小规模项目的快速开发。使用上，与Ruby的Sinatra，Python的Web.py十分类似。
