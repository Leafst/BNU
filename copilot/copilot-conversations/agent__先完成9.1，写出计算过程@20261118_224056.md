---
epoch: 1795012856811
mode: agent
backendId: codex
sessionId: "01a1ef1a-1731-7c02-a212-f17ebfad9052"
topic: "先完成9.1，写出计算过程"
model: '{"baseModelId":"gpt-6.1-sol","effort":"medium"}'
tags:
  - copilot-conversation
usage: '{"usedTokens":53509,"contextWindow":828400,"updatedAt":1795019447057}'
lastAccessedAt: 1795015144064
---

**user**: 先完成9.1，写出计算过程
<!-- copilot-message {"notes":["资产定价/课件/《资产定价》练习题.pdf"]} -->
[Timestamp: 2026/11/18 22:40:56]

**ai**: 我先查看练习题中第 9.1 题的题目，再逐步写出计算过程。我会使用 PDF 阅读流程提取题目，并核对题目中的数值和条件。下面求解 [[《资产定价》练习题]] 的 **9.1**。设状态 $a$、$b$ 的概率分别为 $p$、$1-p$，并假设 $0<p<1$。记两只证券在第 0 期的价格为 $S_1$、$S_2$。

题中各参与者的股票禀赋满足 $\sum_k b_k=1$，因此经济的总禀赋为

$$
C_0=C,\qquad C_{1a}=uC,\qquad C_{1b}=dC.
$$

### （a）证明证券市场完全

两只证券在两个状态下的支付矩阵为

$$
X=
\begin{pmatrix}
1&uC\\
1&dC
\end{pmatrix}.
$$

其行列式为

$$
\det X=C(d-u)\ne 0,
$$

因为 $C>0$ 且 $u>d$。所以 $X$ 满秩，两只证券可以复制任意两个状态下的支付向量，**证券市场是完全的**。

### （b）求最优消费与投资选择

先设状态 $a$、$b$ 的 Arrow-Debreu 价格分别为 $q_a$、$q_b$。参与者 $k$ 的初始财富为

$$
w_k=b_kC+b_kS_2=b_k(C+S_2).
$$

他的优化问题可以写为

$$
\begin{aligned}
\max_{c_{k,0},c_{k,1a},c_{k,1b}}\quad&
\log c_{k,0}
+\rho\left[p\log c_{k,1a}+(1-p)\log c_{k,1b}\right],\\
\text{s.t.}\quad&
c_{k,0}+q_ac_{k,1a}+q_bc_{k,1b}=w_k.
\end{aligned}
$$

令预算约束的拉格朗日乘数为 $\lambda_k$，一阶条件为

$$
\frac1{c_{k,0}}=\lambda_k,\qquad
\frac{\rho p}{c_{k,1a}}=\lambda_kq_a,\qquad
\frac{\rho(1-p)}{c_{k,1b}}=\lambda_kq_b.
$$

将其代回预算约束，得到

$$
\frac{1+\rho}{\lambda_k}=w_k.
$$

因此，**给定价格时**，最优消费为

$$
c_{k,0}=\frac{w_k}{1+\rho},\qquad
c_{k,1a}=\frac{\rho p\,w_k}{(1+\rho)q_a},\qquad
c_{k,1b}=\frac{\rho(1-p)w_k}{(1+\rho)q_b}.
$$

下面求出均衡价格，再代回得到均衡投资选择。

### （c）求均衡证券价格

由于每位参与者的财富都是总财富 $C+S_2$ 的 $b_k$ 倍，最优消费也按 $b_k$ 的比例分配。结合各期、各状态的市场出清条件：

$$
\sum_k c_{k,0}=C,\qquad
\sum_k c_{k,1a}=uC,\qquad
\sum_k c_{k,1b}=dC,
$$

可得均衡消费为

$$
\boxed{
c_{k,0}=b_kC,\qquad
c_{k,1a}=b_kuC,\qquad
c_{k,1b}=b_kdC.
}
$$

将这些消费代入一阶条件，例如

$$
q_a=\rho p\frac{c_{k,0}}{c_{k,1a}},
$$

得到均衡状态价格：

$$
\boxed{
q_a=\frac{\rho p}{u},\qquad
q_b=\frac{\rho(1-p)}{d}.
}
$$

证券价格等于各状态支付的状态价格之和。因此，无风险证券的价格为

$$
\boxed{
S_1=q_a+q_b
=\rho\left(\frac p u+\frac{1-p}{d}\right).
}
$$

股票的价格为

$$
\boxed{
S_2=q_a(uC)+q_b(dC)=\rho C.
}
$$

均衡时，参与者 $k$ 持有 $\theta_{k,1}$ 单位无风险证券和 $\theta_{k,2}$ 单位股票，须满足

$$
\begin{cases}
\theta_{k,1}+uC\theta_{k,2}=b_kuC,\\
\theta_{k,1}+dC\theta_{k,2}=b_kdC.
\end{cases}
$$

两式相减并利用 $u\ne d$，得到

$$
\boxed{
\theta_{k,1}^{*}=0,\qquad \theta_{k,2}^{*}=b_k.
}
$$

即各参与者在均衡中保留自己的初始证券禀赋。此时无风险证券的总持有量为 $0$，股票的总持有量为 $\sum_k b_k=1$，两个市场均出清。

### （d）与二叉树期权定价模型比较

以股票的**均衡初始价格** $S_2=\rho C$ 为基准，股票未来价格的上、下倍率分别是

$$
U=\frac{uC}{S_2}=\frac u\rho,\qquad
D=\frac{dC}{S_2}=\frac d\rho.
$$

无风险总收益率为

$$
R_f=\frac1{S_1}.
$$

定义风险中性概率

$$
\widetilde p=\frac{q_a}{q_a+q_b}
=\frac{p/u}{p/u+(1-p)/d}
=\frac{pd}{pd+(1-p)u}.
$$

由于 $0<p<1$ 且 $u>d>0$，有 $0<\widetilde p<1$；同时它满足标准二叉树模型的关系

$$
\widetilde p=\frac{R_f-D}{U-D}.
$$

因此，任何未来支付为 $(Y_a,Y_b)$ 的证券，都可按二叉树风险中性定价公式计算：

$$
\boxed{
Y_0=\frac1{R_f}
\left[\widetilde pY_a+(1-\widetilde p)Y_b\right].
}
$$

两者的定价形式一致。这里的区别在于：本题从参与者的偏好和禀赋出发，**在一般均衡中求出了股票价格、无风险利率和风险中性概率**。此外，因为高消费状态 $a$ 中消费的边际效用较低，

$$
\widetilde p<p,
$$

所以定价时赋予高消费状态的风险中性概率低于其真实概率。
<!-- copilot-message {"tools":["Read file 'SKILL.md' (read)","pdftotext -layout 'D:/BNU/资产定价/课件/《资产定价》练习题.pdf' - (execute)"]} -->
[Timestamp: 2026/11/18 22:40:56]

**user**: 为什么要用AD价格求解呢，不觉得很绕吗
<!-- copilot-message {"notes":["资产定价/课件/《资产定价》练习题.pdf"]} -->
[Timestamp: 2026/11/18 22:44:29]

**ai**: 你说得对，**这题不必先引入 AD 价格**。我之前是利用完全市场，把问题转成状态消费选择；这样做比较通用，但这题各参与者的偏好相同、禀赋又成比例，直接用证券持仓求均衡更简洁。

设证券 1、2 的价格分别为 $S_1,S_2$，参与者 $k$ 选择持仓 $\theta_1,\theta_2$。他的消费是

$$
\begin{aligned}
c_{k,0}&=b_kC+b_kS_2-\theta_1S_1-\theta_2S_2,\\
c_{k,1a}&=\theta_1+\theta_2uC,\\
c_{k,1b}&=\theta_1+\theta_2dC.
\end{aligned}
$$

将其代入效用函数，对两种证券持仓求一阶条件：

$$
-\frac{S_1}{c_{k,0}}
+\rho\left(\frac p{c_{k,1a}}+\frac{1-p}{c_{k,1b}}\right)=0,
$$

$$
-\frac{S_2}{c_{k,0}}
+\rho\left(\frac{puC}{c_{k,1a}}
+\frac{(1-p)dC}{c_{k,1b}}\right)=0.
$$

接着利用本题的对称结构：各参与者拥有相同比例的当期和未来禀赋。可以**猜测并验证**，均衡时他们保留原有禀赋，即

$$
\theta_1=0,\qquad \theta_2=b_k.
$$

于是消费为

$$
c_{k,0}=b_kC,\qquad
c_{k,1a}=b_kuC,\qquad
c_{k,1b}=b_kdC.
$$

代入两条一阶条件，直接得到

$$
\boxed{S_1=\rho\left(\frac p u+\frac{1-p}{d}\right)},
\qquad
\boxed{S_2=\rho C}.
$$

在这组价格下，猜测的持仓满足最优化条件；同时，所有人的无风险证券持仓加总为 $0$，股票持仓加总为 $\sum_k b_k=1$，市场出清。因此它确实是均衡。

所以这题最直接的思路是：**写消费 → 对证券持仓求一阶条件 → 猜测保留禀赋 → 验证价格和市场出清**。AD 价格不是必须的，只是在处理更一般的状态支付或后面推导风险中性概率时比较方便。
[Timestamp: 2026/11/18 22:44:29]

**user**: 回到刚开始c的求解，为什么直接从出清推导出均衡消费了
<!-- copilot-message {"notes":["资产定价/课件/《资产定价》练习题.pdf"]} -->
[Timestamp: 2026/11/18 22:49:04]

**ai**: 你的疑问很关键：**仅凭市场出清，不能直接推出每个人的均衡消费。** 我之前省略了一个关键步骤：先由最优消费公式和禀赋结构，证明每个人消费的比例都是 $b_k$，再用市场出清确定消费总量。

具体来说，参与者 $k$ 的初始财富为

$$
w_k=b_k(C+S_2).
$$

因为所有参与者面对相同的价格，也有相同的效用函数，上一问求出的最优消费满足

$$
c_{k,0}=\frac{w_k}{1+\rho},\qquad
c_{k,1a}=\frac{\rho p\,w_k}{(1+\rho)q_a},\qquad
c_{k,1b}=\frac{\rho(1-p)w_k}{(1+\rho)q_b}.
$$

注意，每一项都与 $w_k$ 成正比，而 $w_k$ 又与 $b_k$ 成正比。因此，对于任何两位参与者 $i,j$，

$$
\frac{c_{i,0}}{c_{j,0}}
=\frac{c_{i,1a}}{c_{j,1a}}
=\frac{c_{i,1b}}{c_{j,1b}}
=\frac{b_i}{b_j}.
$$

再利用 $\sum_k b_k=1$，可知每个人在各期、各状态的消费都占总消费的 $b_k$：

$$
c_{k,0}=b_k\sum_j c_{j,0},\qquad
c_{k,1s}=b_k\sum_j c_{j,1s}\quad(s=a,b).
$$

**这时才使用市场出清。** 经济的总禀赋分别为 $C$、$uC$、$dC$，所以

$$
\sum_j c_{j,0}=C,\qquad
\sum_j c_{j,1a}=uC,\qquad
\sum_j c_{j,1b}=dC.
$$

代回即得

$$
\boxed{
c_{k,0}=b_kC,\qquad
c_{k,1a}=b_kuC,\qquad
c_{k,1b}=b_kdC.
}
$$

换句话说，**最优化决定了各人的消费份额，市场出清决定了消费总量**。如果只知道市场出清，例如只知道 $\sum_k c_{k,0}=C$，那么还可能有许多不同的个人消费分配，不能单独得出 $c_{k,0}=b_kC$。
[Timestamp: 2026/11/18 22:49:04]

**user**: 这里的0期市场出清为什么只有C，没有证券2
<!-- copilot-message {"notes":["资产定价/课件/《资产定价》练习题.pdf"]} -->
[Timestamp: 2026/11/18 23:29:04]

**ai**: 因为这里的市场出清是在算**第 0 期消费品的总量**。经济中第 0 期的消费品禀赋只有

$$
\sum_k b_kC=C.
$$

证券 2 虽然在第 0 期有价格，也可以交易，但它本身不是第 0 期消费品。它代表的是**第 1 期**取得消费品的权利：状态 $a$ 下支付 $uC$，状态 $b$ 下支付 $dC$。因此，第 0 期消费品市场的出清条件是

$$
\boxed{\sum_k c_{k,0}=C.}
$$

你可能会疑惑：每个人的预算里不是有股票财富 $b_kS_2$ 吗？确实有，但那是股票可以卖给其他参与者换取的财富。从整个经济来看，买股票的人支付的消费品，正好是卖股票的人收到的消费品，交易本身不会创造额外的第 0 期消费品。

把所有人的第 0 期预算式加总，可以看得更清楚：

$$
\sum_k c_{k,0}
=
\underbrace{\sum_k b_kC}_{C}
+\underbrace{S_2\sum_k b_k}_{S_2}
-\underbrace{S_2\sum_k\theta_{k,2}}_{S_2}
-\underbrace{S_1\sum_k\theta_{k,1}}_{0}.
$$

这里用了证券市场出清：

$$
\sum_k\theta_{k,2}=\sum_k b_k=1,\qquad
\sum_k\theta_{k,1}=0.
$$

因此股票的初始价值和最终持有价值在加总后抵消，得到

$$
\sum_k c_{k,0}=C+S_2-S_2=C.
$$

到了第 1 期，股票才产生消费品支付，所以对应的总消费分别是 $uC$ 和 $dC$。
[Timestamp: 2026/11/18 23:29:04]

**user**: 继续完成9.2
<!-- copilot-message {"notes":["资产定价/课件/《资产定价》练习题.pdf"]} -->
[Timestamp: 2026/11/18 23:33:33]

**ai**: 继续使用 9.1 的结果。设第 1 期的消费增长率为

$$
g=\frac{C_1}{C_0}
=\begin{cases}
u,&\text{概率为 }p,\\
d,&\text{概率为 }1-p,
\end{cases}
$$

其中 $C_0=C$。记其均值和方差分别为

$$
m=E[g]=pu+(1-p)d,\qquad
v=\operatorname{Var}(g)=p(1-p)(u-d)^2.
$$

### （a）构建代表性参与者

考虑中央计划者将每个状态下的总消费 $C_t$ 分配给 $K$ 个参与者，最大化加权效用：

$$
\max_{\{c_k\}}\sum_{k=1}^K\lambda_k U_k(c_k),
\qquad
\text{s.t.}\quad \sum_{k=1}^Kc_{k,t}=C_t.
$$

先在任意一期、任意状态下考察消费分配。由于各参与者的单期效用均为对数形式，对 $c_{k,t}$ 的一阶条件给出

$$
\frac{\lambda_k}{c_{k,t}}=\eta_t,
$$

其中 $\eta_t$ 是该期或该状态资源约束的乘数。因此

$$
c_{k,t}=\frac{\lambda_k}{\eta_t}.
$$

若将权重标准化为 $\sum_k\lambda_k=1$，由资源约束可得

$$
\boxed{c_{k,t}=\lambda_k C_t.}
$$

将它代回加权效用，得到代表性参与者的效用函数：

$$
\begin{aligned}
U^{R}(C_0,C_1)
&=\sum_k\lambda_k
\left[\log(\lambda_kC_0)+\rho E\log(\lambda_kC_1)\right]\\
&=\log C_0+\rho E[\log C_1]
 +(1+\rho)\sum_k\lambda_k\log\lambda_k.
\end{aligned}
$$

最后一项与消费选择无关，可以省略。因此，代表性参与者的偏好可表示为

$$
\boxed{
U^{R}(C_0,C_1)=\log C_0+\rho E[\log C_1].
}
$$

其总禀赋为

$$
C_0=C,\qquad
C_{1a}=uC,\qquad
C_{1b}=dC.
$$

### （b）计算各参与者的权重

9.1 中求得的均衡消费为

$$
c_{k,0}=b_kC,\qquad
c_{k,1a}=b_kuC,\qquad
c_{k,1b}=b_kdC.
$$

也就是说，参与者 $k$ 在每个时期、每个状态下都消费总量的 $b_k$。与中央计划者的分配规则 $c_{k,t}=\lambda_kC_t$ 比较，在 $\sum_k\lambda_k=1$ 的标准化下：

$$
\boxed{\lambda_k=b_k.}
$$

权重取决于参与者的禀赋份额 $b_k$。原因是大家的偏好相同，而参与者 $k$ 拥有每一期、每个状态下总禀赋的同一比例 $b_k$；均衡中他的消费也保持这一比例。

### （c）代表性参与者的偏好与禀赋分布无关

改变各参与者的 $b_k$，会改变中央计划者问题中的权重，也会改变每个人的消费份额。但只要 $\sum_k b_k=1$，总禀赋仍是

$$
(C_0,C_{1a},C_{1b})=(C,uC,dC).
$$

同时，代表性参与者效用中含权重的部分

$$
(1+\rho)\sum_k b_k\log b_k
$$

只是一个与总消费无关的常数。因此，无论 $b_k$ 如何分布，代表性参与者的偏好都可以表示为

$$
\boxed{U^{R}=\log C_0+\rho E[\log C_1].}
$$

这里说的“无关”是指**偏好关系**无关：效用函数可能相差一个常数，但这个常数不影响选择和资产定价。

### （d）用 CCAPM 为两只证券定价

代表性参与者的单期效用为 $u(C)=\log C$，所以边际效用为 $u'(C)=1/C$。随机贴现因子为

$$
M=\rho\frac{u'(C_1)}{u'(C_0)}
=\rho\frac{C_0}{C_1}
=\frac{\rho}{g}.
$$

对于未来支付为 $X$ 的证券，CCAPM 定价公式为

$$
S=E[MX].
$$

**证券 1** 在两个状态下都支付 $1$，因此

$$
\begin{aligned}
S_1
&=E[M]\\
&=\rho\left(\frac p u+\frac{1-p}{d}\right).
\end{aligned}
$$

故

$$
\boxed{S_1=\rho\left(\frac p u+\frac{1-p}{d}\right).}
$$

**证券 2** 的未来支付就是总消费 $C_1$，因此

$$
\begin{aligned}
S_2
&=E[MC_1]
=E\left[\rho\frac{C_0}{C_1}C_1\right]\\
&=\rho C_0.
\end{aligned}
$$

故

$$
\boxed{S_2=\rho C.}
$$

这与 9.1 中的均衡价格一致。

### （e）计算无风险利率和股票风险溢价

证券 1 的价格为 $S_1$，未来确定支付 $1$，所以无风险总收益率为

$$
\boxed{
R_f=1+r_f
=\frac{1}{\rho\left(p/u+(1-p)/d\right)}.
}
$$

股票的总收益率为

$$
R_2=\frac{C_1}{S_2}
=\frac{gC}{\rho C}
=\frac g\rho.
$$

因此

$$
E[R_2]=\frac m\rho.
$$

股票风险溢价等于其期望收益率减去无风险收益率；用总收益率或净收益率计算，差额相同：

$$
\begin{aligned}
E[r_2]-r_f
&=E[R_2]-R_f\\
&=\frac{m}{\rho}
-\frac{1}{\rho\left(p/u+(1-p)/d\right)}.
\end{aligned}
$$

为了化简，注意到

$$
\frac p u+\frac{1-p}{d}
=\frac{pd+(1-p)u}{ud}.
$$

而

$$
pd+(1-p)u=u+d-m,\qquad
v=p(1-p)(u-d)^2=(u-m)(m-d),
$$

所以

$$
m(u+d-m)=ud+v.
$$

由此可得

$$
\frac{1}{p/u+(1-p)/d}
=\frac{ud}{u+d-m}
=m-\frac{v}{u+d-m}.
$$

因此结果可以写为

$$
\boxed{
R_f=\frac1\rho\left(m-\frac{v}{u+d-m}\right),
\qquad
E[r_2]-r_f=\frac{v}{\rho(u+d-m)}.
}
$$

其中 $u+d-m=pd+(1-p)u>0$。当消费增长没有风险，即 $u=d$ 或 $p=0,1$ 时，$v=0$，风险溢价为零。

### （f）解释各变量的影响

- **当前消费水平 $C$：** 无风险利率和股票风险溢价都不依赖 $C$。虽然股票价格 $S_2=\rho C$ 随 $C$ 增长，但股票未来支付也同比例增长，因而收益率不变。

- **时间偏好参数 $\rho$：** 固定消费增长率分布时，$R_f$、股票期望总收益率和风险溢价均与 $1/\rho$ 成正比。$\rho$ 越高，参与者越重视未来消费，愿意支付更高的证券价格，因此这些总收益率及其差额越低。

- **消费增长率的期望值和方差：** 不能只根据 $m$ 和 $v$ 两个数，一般性地确定本题的利率和风险溢价：公式还包含 $u+d-m$，即分布的其他信息。不过，在说明比较方式后，可以得到明确结论。例如，**固定 $p$ 和均值 $m$，扩大 $u$ 与 $d$ 的距离**时，$v$ 上升；由于 $1/g$ 是凸函数，$E[1/g]$ 上升，因此 $R_f$ 下降。与此同时，$E[R_2]=m/\rho$ 不变，所以股票风险溢价上升。

最后一点反映了预防性储蓄：消费增长风险变大时，无风险证券在未来消费较低的状态下尤其有价值，其价格上升、收益率下降。
[Timestamp: 2026/11/18 23:33:33]

**user**: 9.2的 表达和我的课件不太类似啊。
<!-- copilot-message {"notes":["资产定价/课件/09-完全市场中一般均衡的性质.pdf"]} -->
[Timestamp: 2026/11/19 00:08:39]

**ai**: 我先对照你这份课件里的代表性参与者和定价公式，再把 9.2 的解答改成课件的表达方式。课件确实用了不同的符号：中央计划者权重记为 $\mu_k$，个人预算约束的乘数记为 $\lambda_k$，随机贴现因子记为 $\tilde\pi$。我之前用 $\lambda_k$ 表示权重、用 $M$ 表示贴现因子，容易和课件混淆；下面按课件的符号重新对应。我对照了课件。**之前的主要结果一致，但符号和推导顺序没有跟课件对应，尤其把课件的 $\lambda_k$ 用成了中央计划者权重，确实容易混淆。** 下面按 [[09-完全市场中一般均衡的性质]] 第 7、23、26—27 页的表达重新整理。

**（a）构建代表性参与者**

课件用 $\mu_k$ 表示中央计划者给参与者 $k$ 的权重。中央计划者的问题是

$$
\max_{\{c_k\}}\sum_k\mu_k
\left\{\log c_{k,0}
+\rho\left[p\log c_{k,1a}+(1-p)\log c_{k,1b}\right]\right\},
$$

满足各期、各状态的资源约束

$$
\sum_kc_{k,0}=C,\qquad
\sum_kc_{k,1a}=uC,\qquad
\sum_kc_{k,1b}=dC.
$$

将权重标准化为 $\sum_k\mu_k=1$。给定任意总消费量 $x$，中央计划者的单期分配问题是

$$
u(x)=\max_{\sum_kc_k=x}\sum_k\mu_k\log c_k.
$$

一阶条件为

$$
\frac{\mu_k}{c_k}=\eta
\quad\Rightarrow\quad
c_k=\frac{\mu_k}{\eta}.
$$

利用 $\sum_kc_k=x$，得 $\eta=1/x$，因此

$$
c_k=\mu_kx.
$$

代回目标函数：

$$
u(x)=\sum_k\mu_k\log(\mu_kx)
=\log x+\sum_k\mu_k\log\mu_k.
$$

省略不影响偏好的常数，代表性参与者具有单期效用

$$
\boxed{u(x)=\log x.}
$$

所以其期望效用为

$$
\boxed{
U^R=\log C_0+
\rho\left[p\log C_{1a}+(1-p)\log C_{1b}\right],
}
$$

禀赋是经济的总禀赋 $(C,uC,dC)$。

这也对应课件第 23 页的“加总”：对数效用是其中 HARA 效用在 $\gamma\to1$ 时的形式，代表性参与者仍具有对数效用。

**（b）权重是多少，依赖于什么？**

课件第 7 页区分了两种乘数：

- $\lambda_k$：个人预算约束的拉格朗日乘数；
- $\mu_k$：中央计划者的效用权重。

个人最优化的一阶条件是

$$
u'(c_{k,0})=\lambda_k.
$$

本题 $u'(c)=1/c$，而 9.1 已得 $c_{k,0}=b_kC$，所以

$$
\lambda_k=\frac1{b_kC}.
$$

课件中中央计划者与个人最优化的对应关系为

$$
\frac{\phi'_0}{\mu_k}=\lambda_k
\quad\Rightarrow\quad
\mu_k=\frac{\phi'_0}{\lambda_k}.
$$

因此，**权重与个人财富的边际效用成反比**：

$$
\mu_k\propto\frac1{\lambda_k}=b_kC.
$$

标准化后，

$$
\boxed{\mu_k=b_k.}
$$

所以权重取决于初始禀赋份额。财富越多的人，财富的边际效用 $\lambda_k$ 越低；要让中央计划者的最优分配与该市场均衡一致，就需要赋予他更大的权重 $\mu_k$。

**（c）为什么代表性参与者的偏好与禀赋分布无关？**

由（a）可知，

$$
u(x)=\log x+\sum_k\mu_k\log\mu_k.
$$

禀赋分布通过 $\mu_k=b_k$ 影响第二项，但第二项与 $x$ 无关。因此，无论禀赋怎样分布，都有

$$
\boxed{u'(x)=\frac1x.}
$$

代表性参与者的偏好可统一表示为对数效用，用于定价的边际效用也不受分布影响。这正是课件所说的“存在加总”。

**（d）按照课件的 CCAPM 定价**

课件第 26 页从证券持仓的一阶条件得到

$$
S_ju'(C_0)
=\rho E\!\left[u'(\widetilde C_1)\widetilde X_j\right].
$$

第 27 页定义随机贴现因子

$$
\widetilde\pi
=\rho\frac{u'(\widetilde C_1)}{u'(C_0)}.
$$

本题中，

$$
\boxed{
\widetilde\pi=\rho\frac{C_0}{\widetilde C_1}
=\begin{cases}
\rho/u,&a,\\
\rho/d,&b.
\end{cases}
}
$$

于是 $S_j=E[\widetilde\pi\widetilde X_j]$。

证券 1 的支付恒为 $1$，故

$$
\boxed{
S_1=E[\widetilde\pi]
=\rho\left(\frac p u+\frac{1-p}{d}\right).
}
$$

证券 2 的支付为 $\widetilde C_1$，故

$$
\boxed{
S_2=E[\widetilde\pi\widetilde C_1]
=\rho C.
}
$$

**（e）无风险利率与股票风险溢价**

按照课件的记号，

$$
E[\widetilde\pi]=\frac1{1+r_f},
$$

因此

$$
\boxed{
r_f=
\frac1{\rho\left(p/u+(1-p)/d\right)}-1.
}
$$

股票净收益率为

$$
\widetilde r_2
=\frac{\widetilde C_1}{S_2}-1
=\frac{\widetilde C_1/C_0}{\rho}-1,
$$

所以

$$
E[\widetilde r_2]=\frac{pu+(1-p)d}{\rho}-1.
$$

风险溢价为

$$
\boxed{
E[\widetilde r_2]-r_f
=\frac1\rho\left[
pu+(1-p)d-\frac1{p/u+(1-p)/d}
\right].
}
$$

进一步化简：

$$
\boxed{
E[\widetilde r_2]-r_f
=\frac{p(1-p)(u-d)^2}
{\rho[pd+(1-p)u]}>0.
}
$$

这也可以直接联系课件第 27 页的 CCAPM：

$$
\boxed{
E[\widetilde r_2]-r_f
=-(1+r_f)\operatorname{Cov}
(\widetilde\pi,\widetilde r_2).
}
$$

高消费状态下，股票收益率高，但边际效用及贴现因子低，故协方差为负，股票具有正风险溢价。

**（f）经济解释**

- **当前消费水平 $C$：** 固定增长率分布时，利率和风险溢价都不依赖 $C$，因为贴现因子只取决于消费增长率 $\widetilde C_1/C_0$。
- **预期消费增长：** 若将 $u,d$ 同时乘以 $t>1$，消费增长整体提高，则 $1+r_f$ 和风险溢价都扩大为原来的 $t$ 倍。未来消费更充裕，未来支付的边际效用降低，证券要求的收益率提高。
- **消费增长风险：** 固定 $p$ 和平均增长率，扩大 $u,d$ 的差距，会提高 $E[C_0/\widetilde C_1]$，从而降低无风险利率；股票的期望收益率保持不变，因此风险溢价提高。
- **折现系数 $\rho$：** 固定增长率分布，$\rho$ 越大，参与者越重视未来，证券价格越高，无风险利率和股票风险溢价越低。

讨论均值、方差的影响时，需要像上面这样说明如何改变分布；仅给出均值和方差，一般不足以确定 $E[C_0/\widetilde C_1]$。
<!-- copilot-message {"tools":["pdftotext -layout 'D:/BNU/资产定价/课件/09-完全市场中一般均衡的性质.pdf' - (execute)","@' import fitz, base64 from PIL import Image import io doc=fitz.open('D:/BNU/资产定价/课件/09-完全市场中一般均衡的性质.pdf') pages=[5,6,16,19,22,23,25,26,29] imgs=[] for n in pages: pix=doc[n].get_pixmap(matrix=fitz.Matrix(1.3,1.3)) imgs.append(Image.open(io.BytesIO(pix.tobytes('png'))).convert('RGB')) w=max(i.width for i in imgs) out=Image.new('RGB',(w*3,max(i.height for i in imgs)*3),'white') for j,im in enumerate(imgs):out.paste(im,((j%3)*w,(j//3)*max(i.height for i in imgs))) buf=io.BytesIO();out.save(buf,format='PNG');print(base64.b64encode(buf.getvalue()).decode()) '@ | python - (execute)","@' import subprocess,base64,json p='D:/BNU/资产定价/课件/09-完全市场中一般均衡的性质.pdf' results=[] for n in [7,17,23,26,27]: x=subprocess.run(['pdftoppm','-f',str(n),'-l',str(n),'-scale-to','1100','-singlefile','-png',p],stdout=subprocess.PIPE,stderr=subprocess.PIPE) results.append({'page':n,'image':base64.b64encode(x.stdout).decode(),'error':x.stderr.decode(errors='replace')}) print(json.dumps(results)) '@ | python - (execute)","@' import subprocess,base64,json,pathlib p=str(next(pathlib.Path('D:/BNU').rglob('09-*.pdf'))) results=[] for n in [7,17,23,26,27]: x=subprocess.run(['pdftoppm','-f',str(n),'-l',str(n),'-scale-to','1100','-singlefile','-png',p],stdout=subprocess.PIPE,stderr=subprocess.PIPE) results.append({'page':n,'image':base64.b64encode(x.stdout).decode(),'error':x.stderr.decode(errors='replace')}) print(json.dumps(results)) '@ | python - (execute)","@' import subprocess,base64,json,pathlib p=str(next(pathlib.Path('D:/BNU').rglob('09-*.pdf'))) a=[] for n in [5,6,24,30]: x=subprocess.run(['pdftoppm','-f',str(n),'-l',str(n),'-scale-to','1100','-singlefile','-png',p],stdout=subprocess.PIPE) a.append({'page':n,'image':base64.b64encode(x.stdout).decode()}) print(json.dumps(a)) '@ | python - (execute)"]} -->
[Timestamp: 2026/11/19 00:08:39]

**user**: f的经济解释再审审题
<!-- copilot-message {"notes":["资产定价/课件/《资产定价》练习题.pdf"]} -->
[Timestamp: 2026/11/19 00:18:36]

**ai**: 确实，（f）要求分别讨论**当前消费水平、消费增长率的期望值、消费增长率的方差和折现系数**。我之前把 $u,d$ 同比例放大，会同时改变均值和方差，不能用它说明“期望值单独变化”的影响。

应当固定概率 $p$，分别考察均值、方差的变化。记

$$
m=E\left[\frac{\widetilde C_1}{C_0}\right]
=pu+(1-p)d,\qquad
v=\operatorname{Var}\left(\frac{\widetilde C_1}{C_0}\right)
=p(1-p)(u-d)^2.
$$

再记

$$
B=pd+(1-p)u.
$$

由前面的计算，

$$
\boxed{
1+r_f=\frac1\rho\left(m-\frac vB\right),\qquad
E[\widetilde r_2]-r_f=\frac{v}{\rho B}.
}
$$

注意 $B$ 也随 $m,v$ 变化。固定 $p$ 时，

$$
B=m+(1-2p)\sqrt{\frac{v}{p(1-p)}}.
$$

**① 当前消费水平 $C_0$**

固定消费增长率的分布时，利率和风险溢价都与 $C_0$ 无关。

原因是对数效用下

$$
\widetilde\pi=\rho\frac{C_0}{\widetilde C_1}
=\frac{\rho}{\widetilde C_1/C_0},
$$

只取决于增长率。当前消费与未来消费同比例提高，不改变跨期边际替代率。

**② 消费增长率的期望值 $m$：保持方差不变**

固定 $p,v$，提高 $m$，相当于将 $u,d$ 同时增加相同数额。此时

$$
\frac{\partial r_f}{\partial m}
=\frac1\rho\left(1+\frac v{B^2}\right)>0,
$$

$$
\frac{\partial\big(E[\widetilde r_2]-r_f\big)}{\partial m}
=-\frac{v}{\rho B^2}<0.
$$

因此，**预期消费增长提高，无风险利率上升，股票风险溢价下降。**

未来消费更充裕，参与者希望将部分未来资源转移到当前、减少储蓄，均衡利率上升。同时，在绝对波动幅度不变的条件下，更高的未来消费水平降低了相对消费风险，股票所需的风险补偿减少。

**③ 消费增长率的方差 $v$：保持期望值不变**

固定 $p,m$，扩大 $u,d$ 的差距，可以得到

$$
\frac{\partial\big(E[\widetilde r_2]-r_f\big)}{\partial v}
=\frac{u+d}{2\rho B^2}>0.
$$

因为股票的期望总收益率 $m/\rho$ 保持不变，

$$
\frac{\partial r_f}{\partial v}
=-\frac{u+d}{2\rho B^2}<0.
$$

因此，**消费增长风险增加，无风险利率下降，股票风险溢价上升。**

风险增加使参与者更希望储蓄以防范低消费状态，推高无风险证券价格、压低利率；而股票恰好在低消费状态支付较少，需要更高的风险补偿。

**④ 时间折现系数 $\rho$**

固定增长率分布，

$$
1+r_f\propto\frac1\rho,\qquad
E[\widetilde r_2]-r_f\propto\frac1\rho.
$$

所以 **$\rho$ 提高，无风险利率下降，股票风险溢价下降。**

$\rho$ 越大，参与者越重视未来消费，愿意为未来支付付出更高价格，从而降低证券收益率。在本题中，两种证券的总收益率均按 $1/\rho$ 缩放，风险溢价也同比例下降。
[Timestamp: 2026/11/19 00:18:36]

**user**: 看下f的问题。作答，这分析一长串我答不了
<!-- copilot-message {"notes":["资产定价/课件/《资产定价》练习题.pdf"]} -->
[Timestamp: 2026/11/19 00:20:22]

**ai**: （f）在概率 $p$ 固定、其他条件不变时：

- **当前消费水平**：无风险利率和股票风险溢价均与其无关，因为对数效用下，定价只取决于消费增长率。
- **消费增长率的期望值提高**（方差不变）：无风险利率上升，股票风险溢价下降。未来消费更充裕，当前储蓄意愿降低，同时相对消费风险减小。
- **消费增长率的方差提高**（期望值不变）：无风险利率下降，股票风险溢价上升。消费风险增加使预防性储蓄增加，也要求股票提供更多风险补偿。
- **时间折现系数 $\rho$ 提高**：无风险利率和股票风险溢价均下降。参与者更加重视未来消费，证券价格提高，要求的收益率降低。
[Timestamp: 2026/11/19 00:20:22]

**user**: 依赖于什么
<!-- copilot-message {"notes":["资产定价/课件/《资产定价》练习题.pdf"]} -->
[Timestamp: 2026/11/19 00:20:38]

**ai**: 无风险利率和股票风险溢价都**依赖于消费增长率的分布（$p,u,d$）和时间折现系数 $\rho$**，与当前消费水平 $C$ 及禀赋在参与者之间的分配 $b_k$ 无关。

$$
r_f=\frac{1}{\rho\left(p/u+(1-p)/d\right)}-1,
$$

$$
E[r_2]-r_f
=\frac{p(1-p)(u-d)^2}{\rho[pd+(1-p)u]}.
$$
[Timestamp: 2026/11/19 00:20:38]

**user**: f的回答稍微解释一下
<!-- copilot-message {"notes":["资产定价/课件/《资产定价》练习题.pdf"]} -->
[Timestamp: 2026/11/19 00:30:37]

**ai**: （f）无风险利率和股票风险溢价依赖于**消费增长率的分布和时间折现系数 $\rho$**，与当前消费水平及个人禀赋份额无关。固定概率 $p$，分别讨论：

- **当前消费水平**：两者均不受影响。对数效用下，随机贴现因子为 $\rho C_0/C_1$，只取决于消费增长率。
- **预期消费增长率提高，方差不变**：无风险利率上升，股票风险溢价下降。未来消费更充裕，储蓄意愿降低；同时相对消费风险减小，所需风险补偿减少。
- **消费增长率的方差提高，均值不变**：无风险利率下降，股票风险溢价上升。参与者增加预防性储蓄，并要求股票提供更多风险补偿。
- **$\rho$ 提高**：无风险利率和股票风险溢价均下降。参与者更重视未来消费，愿意支付更高的证券价格，收益率及其差额随之降低。
[Timestamp: 2026/11/19 00:30:37]