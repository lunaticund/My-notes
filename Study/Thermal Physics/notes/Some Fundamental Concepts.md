# The Thermodynamic Limit
When we consider a system containing a large amount of particles, the fluctuation of the physics quantities to discribe teh system will be erase.

**Extensive variables**: Related to the amount of the substence (V,m)
**Intensive variables**: Affect the internal states of a system (P,T)

The Thermodynamic limit guarantee the addability of the extensive variables and the uniformity of the intensive variables.
$$\text{Microscopic unevenness}\rightarrow\text{Fluctuation}\rightarrow\text{Macroscopic enenness}$$
# Heat
**Definition**:
$$\text{Heat is the energe in transit}$$
Heat and work are the same since they contribute to the same result.

**Heat Capacity**:
$$C=\frac{\mathrm{d}Q}{\mathrm{d}T}$$
Repersent the energe needed to heat the object by one K.
Obversily, $C$ is a extensive variable, and there are two more frequently-uesd intensive heat capacity.
$$\begin{cases}C_n=\frac{C}{n}&\text{Molar heat capacity}\\c=\frac{C}{m}&\text{Specific heat capacity}\end{cases}$$
For gas, we define
$$\begin{cases}C_V=\left(\frac{\mathrm{d}Q}{\mathrm{d}T}\right)_V\\C_P=\left(\frac{\mathrm{d}Q}{\mathrm{d}T}\right)_P\end{cases}$$
Parently $C_P>C_V$, since when we heat the gas, it willdo work to the surrounding as it  expand.
# Temperature
## Thermal Equilibrium
When we put two objects into thermal contact, they will reach the thermal equilibrium spontaneously. And the process is named Thermalization.
Temperature is the physics quantiity to discribe the thermal equilibrium.

**Zeroth Law of Thermodynamics**:
If A is thermal equilibrium to B, B is thermal equilibrium to C, then A is thermal equilibrium to C.
## The Microstates and Macrostsaes
1. A system can be discribed by a large numbers of equally probable microstates.
2. The probabilities of different macrostates can be different since they may correspond to different numbers of microstates.
## A Statistical Definition of Temperature
For a system with energy $E$, we define $\Omega(E)$ as the number of microstates it can stay in. And a system will choose a macrostate with the maximum number of microstates.
**Two fundamental assumptions:**
1. Equal a priori probability: Each microstate has equal probability to occur.
2. Ergodic Hypothesis: The system will explore all the microstates with equal time on each of them in a sufficiently long time.

Consider a system consisting of two systems in thermal contact and holding the total energy $E=E_1+E_2$ .
$$\Omega=\Omega_1(E_1)\cdot\Omega_2(E_2)=\Omega_1(E_1)\cdot\Omega_2(E-E_1)$$
The system stay in the maximum $\Omega$, thus the derivative of it is 0
$$\frac{\mathrm{d}\Omega}{\mathrm{d}E_1}=\Omega_2(E_2)\frac{\mathrm{d}\Omega_1(E_1)}{\mathrm{d}E_1}-\Omega_1(E_1)\frac{\mathrm{d}\Omega_2(E-E_1)}{\mathrm{d}E_2}=0$$
$$\Rightarrow\frac{1}{\Omega_1}\frac{\mathrm{d}\Omega_1}{\mathrm{d}E_1}=\frac{1}{\Omega_2}\frac{\mathrm{d}\Omega_2}{\mathrm{d}E_2}$$
Intergate in the both side, and we get the equilibrium condition.
$$\frac{\mathrm{d}\ln\Omega_1}{\mathrm{d}E_1}=\frac{\mathrm{d}\ln\Omega_2}{\mathrm{d}E_2}$$
Therefore we can define the temperature by
$$\frac{1}{k_BT}=\frac{\mathrm{d}\ln\Omega}{\mathrm{d}E}$$
## Canonical Ensemble
Consider two systems in thermal contact, one of which is enormous and can be seen as a resorvior, and another is the system we really care for. The situation is known as the **canonical ensemble**.
Fix the total energe as $E$, and $\epsilon$ is the part of the smaller system. 
$$\begin{align*}\Omega(E)&=\Omega_1(E-\epsilon)\cdot\Omega_2(\epsilon)\\&\approx\Omega_1(E-\epsilon)\end{align*}$$
Since $\Omega_1\gg\Omega_2$.
Therfore, the probability of the system
$$P(\epsilon)\propto\Omega_1(E-\epsilon)$$
Since $\epsilon\ll E$ , we can prefrom a Taylor expansion to $\ln\Omega_1(E-\epsilon)$
$$\begin{align*}\ln\Omega_1(E-\epsilon)&=\ln\Omega_1(E)-\frac{\mathrm{d}\ln\Omega_1(E)}{\mathrm{d}E}\epsilon+o(\epsilon)\\&=\ln\Omega_1(E)-\frac{\epsilon}{k_BT}\end{align*}$$
$$\Omega_1(E-\epsilon)=\Omega_1(E)\cdot e^{-\frac{\epsilon}{k_BT}}$$
Thus
$$P(\epsilon)\propto e^{-\frac{\epsilon}{k_BT}}$$
This is konwn as **Boltzman distribution**.