---
layout: post
title: Lyapunov Function
date: 2016-11-19 11:26:51 PM 
tags: [专业]  
---

    

在控制理论中，判断系统的指标主要有稳定性、快速性和准确性这三个，稳定性作为控制系统是否能投入使用的最大前提，系统的快速性（带宽）通过频率响应等指标来反映，准确性则表示系统的控制精度。本文主要探讨系统的稳定性这一概念。

在具体的控制系统中，理论控制模型往往可以用或者近似用微分方程或差分方程来描述，因此，对系统稳定性的研究就可以转换为对微分/差分方程稳定性的分析。

对微分/差分方程此类控制理论模型分析稳定性的方法主要有劳斯（Routh）判据、赫尔维兹（Hurwitz）稳定性判据、乃奎斯特（Nyquist）稳定性判据和李雅普诺夫（Lyapunov）稳定性判据。相比而言，前面几种方法和李雅普诺夫第一法主要通过抽象数学方法进行分析，不利于自然语言描述而且本人并没有完全学得透彻，而李雅普诺夫第二法则既可以简单地通过语言描述，并且其概念可以得到进一步推广，因此这里将对后者进行阐述。

回想高中物理题，小球从一定高度的斜坡上开始下滚，计算小球运动到底部时的速度，对于这种题目一种简便的解法是从能量守恒的角度来进行分析，即小球初始位置的动能势能等于小球运动到底部某一时刻的动能势能加上下滑过程中由于摩擦等消耗的能量，由此建立能量方程便可以得出某一确定时刻小球的运动速度。同样的，我们也可以知道，如果小球在一个竖直方向U形的斜坡上滚动，从最高点静止释放，随后让它自由来回滚动，那么由于运动过程中摩擦阻力对能量的消耗，小球速度最终一定会变为零。

李雅普诺夫第二法即是从能量角度来判断系统的稳定性的。如果施加一定输入后，系统的能量随时间衰减，则说明系统的稳定性。假如能找到一个正定（除零点外始终大于零）的李雅普诺夫函数（Lyapunov Function）作为系统的广义能量函数，并且该函数的导数为一个负定（除零点外始终小于零）的函数，则该系统是稳定的。但是找到这样的函数也是一个不确定的问题，如果能找到满足条件的李雅普诺夫函数，则系统稳定；但是如果不能找到，则只能说明无法确定系统的稳定性。

以上是李雅普诺夫稳定性判据在控制领域的说明。

而根据管理学类书《第五项修炼》（彼得·圣吉）里对系统性思维的描述，他将商业策略模式作为一套系统进行一系列分析，一方面印证了我个人对控制论在其他领域（产品理论——最短开发周期快速迭代，自我管理——最小系统的实现和快速迭代修正以及企业管理）中的应用（其实套用的大多都是同一个概念），另一方面也说明了并不只是工程中的问题可以用来做控制系统分析，生活中的许多事情都可以采用系统化的思维来看待和分析（2016.11.16我去参加英语角和同桌伙伴们交谈时也谈到这一点，对应的是那位加拿大计算机教授对学生科研的建议是“do not lost yourself in details, sometimes you need to know the answer of 'what's the purpose of my life', you need to do something else rather than doing research to be more creative.”）。例如书里第三章提到的“厂家-经销商啤酒游戏”，每个人的行为从一个个体来看都是一个合情合理的决策反应，但是却因为信息传递的时间滞后导致了最终整条销售链各个环节的失败，每个人此时都会自然地责怪外部其他环节，但是更有可能的一种原因是这样一种系统的结构决定了这种不稳定性，根本的解决方法是改变系统的结构，而不是简单的互相责备。

除此之外，书中提到的几种商业“基础模型”让我想到了公开课《模型思维》（Model Thinking），后者就是通过介绍各种模型来帮助我们更全面系统地看待身边的世界。十分巧合的是，我在翻看目录发现了“Lyapunov Functions”这一章节。因此我采用这门课里面的内容来说明“Lyapunov Functions”这个系统稳定性判据模型对更广泛的系统的分析。

第一种情况是，存在李雅普诺夫函数F(x)，如果满足条件A1-它有一个最小值，A2-随着时间递增，函数值每次的减小量不少于k，那么在某一点时，这个系统就可以达到稳定状态。对应的情景可以是针对如下问题，为什么城市中不会存在一个地方人挤得爆满，也不会出现一个地方空无人烟的情况，即城市的自我组织能力。这里首先假设人的行为前提是避免人群，那么考虑每个人选择到不同的商店会遇到的人数的总和作为李雅普诺夫函数，则如果我选择到渔具店会比到文具店遇到更少的人群，那么我会选择去渔具店，这种情况下相应的函数值则减小2*我少遇到的人数（因为遇到是相互的），因此，若每个人的行为模式相同，则随着时间的推移，系统一定会达到平衡状态。现实中则是一种动态平衡。用数学语言表述如下：

    F(x), a Lyaponuv function

    A1:  has a minimum value.  

    A2: There is a k > 0 such that if xt+1 ≠ xt, F(xt+1) < F(xt) - k 

    Claim: At some point xt+1 = xt  

第二种情况是，存在李雅普诺夫函数F(x)，如果满足条件A1-它有一个最大值，A2-随着时间递增，函数值每次的增加量不少于k，那么在某一点时，这个系统就可以达到稳定状态。这里对应的情景可以是交易市场，假设在市场中人们只会在个人的高兴值提升的前提下进行交易，那么考虑人群的高兴值总和作为李雅普诺夫函数，那么我每交易一次，函数值都会增加至少一个定值，人群中的高兴值总和存在一个最大值，所以该系统稳定。但是如果考虑北朝鲜和伊拉克交易核武器和石油，他们俩的高兴值增加了，但是世界上其他国家比如美国欧洲和俄罗斯的高兴值下降了，因此无法说明系统整体的高兴值的增加了还是减少了或是振动，因此也就无法判断系统的稳定性。这里的原因被称为外部因素，人的行为影响到了范围外的人或部分。类似的，就可以说，在职场里，可以进行椅子的自由交易，但是进行办公室的自由交易无法达到稳定状态，因为后者存在外部因素（办公室互相隔邻）。用数学语言表述如下：

    F(x), a Lyaponuv function

    A1:  has a maximum value.  

    A2: There is a k > 0 such that if xt+1 ≠ xt, F(xt+1) > F(xt) + k 

    Claim: At some point xt+1 = xt  


20161119