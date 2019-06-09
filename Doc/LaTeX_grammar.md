## **使用LaTeX写公式的基本语法**

*LaTeX* 公式有两种，一种是用在正文中的，一种是单独显示的。正文中的公式用 `$...$` 来定义，单独显示的用 `$$...$$` 来定义，其中 `...` 表示的是*LaTeX* 的公式命令。

例如：

```latex
我们定义$f(x) = \sum_{i=0}^{N}\int_{a}^{b} g(t,i) \text{ d}t$. (行内公式)
或者定义$f(x)$如下（行间公式）: 
$$f(x) = \sum_{i=0}^{N}\int_{a}^{b} g(t,i) \text{ d}t{6}\tag{1}$$
```

得到的结果是：

或者定义f(x)和如下（行间公式）: 

$f(x) = \sum_{i=0}^{N}\int_{a}^{b} g(t,i) \text{ d}t$

$$f(x) = \sum_{i=0}^{N}\int_{a}^{b} g(t,i) \text{ d}t{6}\tag{1}$$

## **基本LaTeX 公式命令**

### **希腊字母**

| 命令1       | 显示1         | 命令2         | 显示2           |
| --------- | ----------- | ----------- | ------------- |
| \alpha    | $\alpha$    | \beta       | $\beta$       |
| \gamma    | $\gamma$    | \delta      | $\delta$      |
| \epsilon  | $\epsilon$  | \varepsilon | $\varepsilon$ |
| \zeta     | $\zeta$     | \eta        | $\eta$        |
| \Gamma    | $\Gamma$    | \Delta      | $\Delta$      |
| \Theta    | $\Theta$    | \theta      | $\theta$      |
| \vartheta | $\vartheta$ | \iota       | $\iota$       |
| \kappa    | $\kappa$    | \lambda     | $\lambda$     |
| \mu       | $\mu$       | \nu         | $\nu$         |
| \xi       | $\xi$       | \Lambda     | $\Lambda$     |
| \Xi       | $\Xi$       | \Pi         | $\Pi$         |
| o         | $o$         | \pi         | $\pi$         |
| \varpi    | $\varpi$    | \rho        | $\rho$        |
| \varrho   | $\varrho$   | \sigma      | $\sigma$      |
| \varsigma | $\varsigma$ | \tau        | $\tau$        |
| \Sigma    | $\Sigma$    | \Upsilon    | $\Upsilon$    |
| \Phi      | $\Phi$      | \upsilon    | $\upsilon$    |
| \phi      | $\phi$      | \varphi     | $\varphi$     |
| \chi      | $\chi$      | \psi        | $\psi$        |
| \omega    | $\omega$    | \Psi        | $\Psi$        |
| \Omega    | $\Omega$    |             |               |

如果使用大写的希腊字母，把命令的首字母变成大写即可，例如 `\Gamma` 输出的是 $\Gamma$。

如果使用斜体大写希腊字母，再在大写希腊字母的*LaTeX*命令前加上var，例如`\varGamma` 生成 $\varGamma$。

例如：

```latex
$$
 \varGamma(x) = \frac{\int_{\alpha}^{\beta} g(t)(x-t)^2\text{ d}t }{\phi(x)\sum_{i=0}^{N-1} \omega_i} \tag{2}
$$
```

生成如下结果：

$$ \varGamma(x) = \frac{\int_{\alpha}^{\beta} g(t)(x-t)^2\text{ d}t }{\phi(x)\sum_{i=0}^{N-1} \omega_i} \tag{2}$$


### **和号和积分号**

和号和积分号比较常用，这里也列出来：

| 命令1               | 显示1                 | 命令2               | 显示2                 |
| ----------------- | ------------------- | ----------------- | ------------------- |
| \sum              | $\sum$              | \int              | $\int$              |
| \sum_{i=1}^{N}    | $\sum_{i=1}^{N}$    | \int_{a}^{b}      | $\int_{a}^{b}$      |
| \prod             | $\prod$             | \iint             | $\iint$             |
| \prod_{i=1}^{N}   | $\prod_{i=1}^{N}$   | \iint_{a}^{b}     | $\iint_{a}^{b}$     |
| \bigcup           | $\bigcup$           | \bigcap           | $\bigcap$           |
| \bigcup_{i=1}^{N} | $\bigcup_{i=1}^{N}$ | \bigcap_{i=1}^{N} | $\bigcap_{i=1}^{N}$ |

### **其它常用命令**

| 命令1              | 显示1              | 命令2         | 显示2           |
| ---------------- | ---------------- | ----------- | ------------- |
| `\sqrt[3]{2}`    | $\sqrt[3]{2}$    | \sqrt{2}    | $\sqrt{2}$    |
| `x^{3}`          | $x^{3}$          | x_{3}       | $x_{3}$       |
| `\lim_{x \to 0}` | $\lim_{x \to 0}$ | \frac{1}{2} | $\frac{1}{2}$ |

**注意**：上标和下标在只有一个字符时，可以不用中括号: `x^2`和`x^{2}`的结果都是 x^2^

## 数学符号

### 数学模式重音符号

| 命令1         | 显示1           | 命令2           | 显示2             |
| ----------- | ------------- | ------------- | --------------- |
| \hat{a}     | $\hat{a}$     | \check{a}     | $\check{a}$     |
| \tilde{a}   | $\tilde{a}$   | \grave{a}     | $\grave{a}$     |
| \dot{a}     | $\dot{a}$     | \ddot{a}      | $\ddot{a}$      |
| \bar{a}     | $\bar{a}$     | \vec{a}       | $\vec{a}$       |
| \widehat{A} | $\widehat{A}$ | \acute{a}     | $\acute{a}$     |
| \breve{a}   | $\breve{a}$   | \widetilde{A} | $\widetilde{A}$ |

### 二元关系

| 命令1         | 显示1           | 命令2         | 显示2           |
| ----------- | ------------- | ----------- | ------------- |
| <           | $<$           | >           | $>$           |
| =           | $=$           | \lep 或 \le  | $\le$         |
| \geq 或 \ge  | $\ge$         | \equiv      | $\equiv$      |
| \ll         | $\ll$         | \gg         | $\gg$         |
| \doteq      | $\doteq$      | \prec       | $\prec$       |
| \succ       | $\succ$       | \sim        | $\sim$        |
| \preceq     | $\preceq$     | \succeq     | $\succeq$     |
| \simeq      | $\simeq$      | \subset     | $\subset$     |
| \supset     | $\supset$     | \approx     | $\approx$     |
| \subseteq   | $\subseteq$   | \supseteq   | $\supseteq$   |
| \cong       | $\cong$       | \sqsubset   | $\sqsubset$   |
| \sqsupset   | $\sqsupset$   | \Join       | $\Join$       |
| \sqsubseteq | $\sqsubseteq$ | \sqsupseteq | $\sqsupseteq$ |
| \bowtie     | $\bowtie$     | \in         | $\in$         |
| \ni 或 \owns | $\ni$         | \propto     | $\propto$     |
| \vdash      | $\vdash$      | \dashv      | $\dashv$      |
| \models     | $\models$     | \mid        | $\mid$        |
| \parallel   | $\parallel$   | \perp       | $\perp$       |
| \smile      | $\smile$      | \frown      | $\frown$      |
| \asymp      | $\asymp$      | :           | $:$           |
| \notin      | $\notin$      | \neq 或 \ne  | $\ne$         |

**注意：**在符号相应命令前加上\not命令，可以得到其否定形式

### 二元运算符

| 命令1              | 显示1                | 命令2            | 显示2              |
| ---------------- | ------------------ | -------------- | ---------------- |
| +                | $+$                | -              | $-$              |
| \pm              | $\pm$              | \mp            | $\mp$            |
| \triangleleft    | $\triangleleft$    | \cdot          | $\cdot$          |
| \div             | $\div$             | \triangleright | $\triangleright$ |
| \times           | $\times$           | \setminus      | $\setminus$      |
| \star            | $\star$            | \cup           | $\cup$           |
| \cap             | $\cap$             | \ast           | $\ast$           |
| \sqcup           | $\sqcup$           | \sqcap         | $\sqcap$         |
| \circ            | $\circ$            | \vee 或 \lor    | $\lor$           |
| \wedge 或 \land   | $\wedge$           | \bullet        | $\bullet$        |
| \oplus           | $\oplus$           | \ominus        | $\ominus$        |
| \diamond         | $\diamond$         | \odot          | $\odot$          |
| \oslash          | $\oslash$          | \uplus         | $\uplus$         |
| \otimes          | $\otimes$          | \bigcirc       | $\bigcirc$       |
| \amalg           | $\amalg$           | \bigtriangleup | $\bigtriangleup$ |
| \bigtriangledown | $\bigtriangledown$ | \dagger        | $\dagger$        |
| \lhd             | $\lhd$             | \rhd           | $\rhd$           |
| \ddagger         | $\ddagger$         | \unlhd         | $\unlhd$         |
| \unrhd           | $\unrhd$           | \wr            | $\wr$            |

## 三角函数

| 命令1 | 显示1  | 命令2 | 显示2  |
| ----- | ------ | ----- | ------ |
| \sin  | $\sin$ | \cos  | $\cos$ |

## 对数函数

| 命令1 | 显示1   | 命令2     | 显示2       |
| ----- | ------- | --------- | ----------- |
| \ln15 | $\ln15$ | \log_2 10 | $\log_2 10$ |
| \lg7  | $\lg7$  |           |             |

