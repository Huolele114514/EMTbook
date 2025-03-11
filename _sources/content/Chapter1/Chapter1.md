# 1.数字仿真基本原理
## 1.1 如何计算RL串联电路的响应？
<center>
<img src="https://notes.sjtu.edu.cn/uploads/upload_3c2ac51b64da4ac5a193b1f963c57f20.png" width="60%">
</center>

<center>图1-1 电阻、电感串联电路</center>

&emsp;&emsp;图1-1所示为电阻、电感串联电路，$U_0 = 10V, R = 1\Omega, L = 0.01H$。当开关S打开时电感元件没有储存能量，在 $t = 0$时，将开关S闭合，有什么方法可以计算这个电路的电流响应呢？

### （1）解析法

&emsp;&emsp;利用电路中的基本电流、电压关系，建立微分方程求解响应。
&emsp;&emsp;电路中电感的电压为 $u_L = L \frac{di}{dt}$，电阻的电压为$u_R = Ri$，对于输入阶跃电压$u(t) = U_0$（阶跃函数），应用基尔霍夫电压定律（KVL）得到：

$$\begin{equation}
U_0 = L \frac{di}{dt} + Ri
\end{equation} $$

&emsp;&emsp;这是一个一阶线性微分方程，解方程得到电流$i(t)$的时间响应：

$$\begin{equation}
i(t) = \frac{U_0}{R} \left( 1 - e^{-\frac{R}{L}t} \right)
\end{equation} $$

其中，时间常数为：$\tau = \frac{L}{R}$。

[练习1-1：RL串联电路电流响应](https://matlab.mathworks.com/open/github/v1?repo=Huolele114514/EX2_1_RL&branch=main&file=EX_2_1_RL.m)
