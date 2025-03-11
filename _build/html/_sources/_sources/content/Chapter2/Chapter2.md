# 2.无穷大电源供电系统三相短路的仿真分析
## 2.1 引言

&emsp;&emsp;在第一章中，我们系统探讨了电力系统数字仿真的基本原理，从简单RL、RC电路的解析解与数值积分法，到复杂电路的状态变量法与数值积分代换法，逐步揭示了如何通过数学建模与计算机编程实现电力系统动态响应的精确仿真。特别地，数值积分代换法通过将储能元件（如电感、电容）转换为离散化的等效导纳与历史电流源，构建Norton等效电路网络，为复杂拓扑的电力系统暂态分析提供了高效且稳定的仿真框架。
&emsp;&emsp;然而，电力系统的实际运行远不止于基础电路的分析。在电力工程实践中，短路故障是最常见且危害性极大的暂态事件之一。其中，三相短路常因电气设备绝缘老化损坏、自然因素（如雷击、恶劣天气）及人为误操作引发，会使短路电流剧增，致电气设备受损、系统电压大幅下降、引发稳定性问题甚至次生灾害。因此通过短路计算确定短路电流大小与分布以选择校验电气设备、评估系统稳定性并为继电保护装置整定计算提供依据，对保障电力系统安全稳定运行意义重大。
&emsp;&emsp;本章将通过数值仿真方法分析无穷大电源供电系统三相短路的暂态过程，计算短路冲击电流、短路电流最大有效值和短路功率，并结合短路故障处理实验，分析故障影响，为后续复杂系统的仿真分析奠定基础。
## 2.2 三相短路过程理论分析 

<center>
<img src="https://notes.sjtu.edu.cn/uploads/upload_0682a6fd0255817265a981600d517c58.png" width="70%">
</center>
<center>图2-1 无穷大电源供电的三相电路</center>

&emsp;&emsp;图2-1所示为《电气工程基础（第二版）下册》第十一章中的无穷大电源供电的三相电路，包含交流电压源、线路电阻和电感。无穷大电源是一种假想的三相对称正弦交流电压源，其电源功率无穷大，内阻抗为零，外电路发生变化时，系统频率和端电压恒定，因此适合用于三相短路过程的分析计算。
&emsp;&emsp;短路发生前，电路处于稳态，以a相为例进行分析。其电压和电流的表达式是：

$$\begin{equation}{u}_{a}={U}_{m}\mathrm{s}\mathrm{i}\mathrm{n}(\omega t+\alpha )\end{equation} $$

$$\begin{equation}{i}_{a}={I}_{m0-}\mathrm{s}\mathrm{i}\mathrm{n}(\omega t+\alpha -{\theta }_{0-})\end{equation} $$


式中：  

$$\begin{equation}
I_{m0} = \frac{U_m}{\sqrt{(R + R')^2 + \omega^2 (L + L')^2}}
\end{equation}  $$

$$\begin{equation}
\theta_0 = \arctan \frac{\omega(L + L')}{R + R'}
\end{equation}  $$

$u_a$、$i_a$ 分别是 $a$ 相电压和电流的瞬时值；$I_{m0-}$ 为短路前的电流幅值；$U_m$ 为电源的电压幅值；$\alpha$ 为电源电势的初相角。  
&emsp;&emsp;$f$点发生突然三相短路时，$a$ 相短路电流表达式（详细推导过程见《电气工程基础（第二版）下册》）：  

$$\begin{equation}
i_a = I_m \sin(\omega t + \alpha - \theta) + \left[ I_{m0} \sin(\alpha - \theta_0) - I_m \sin(\alpha - \theta) \right] e^{-t/T} = i_{pa} + i_{\alpha a}
\end{equation}  $$

式中，$I_m$ 是稳态短路电流的幅值；$\theta = \arctan (\omega L / R)$；$T$ 为直流分量电流衰减时间常数，$T = L / R$；$i_{pa}$ 是短路电流周期分量，$i_{\alpha a}$ 是短路电流非周期分量。
&emsp;&emsp;一般情况下短路回路可近似看成纯电感电路（$\omega L \gg R$），$\theta = 90^\circ$，$\alpha = 0^\circ$ 或 $180^\circ$，如果短路前电路是空载（$I_{m0-} = 0$），则非周期分量的起始值比其他情况都大，即最严重情况，此时 $a$ 相短路电流表达式化简为：  
$$\begin{equation}
i_a = -I_m \cos \omega t + I_m e^{-t/T}
\end{equation}$$
