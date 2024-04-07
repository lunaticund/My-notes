# 1.Heat Engine
## 1.1 Two Statements
**Clausius' statement**:
No process is possible whose sole result is the transfer of heat from a colder to a hotter body.

**Kelvin's statement**:
No process is possible whose sole result is the complete conversation of heat into work.
## 1.2 The Carnot Engine
Carnot cycle consists of
$$
\begin{cases}\text{two adiabatic process}\\\text{two isothermal process}\end{cases}
$$
The high temperature $T_h$, the low temperature $T_l$.
$$
W=Q_{h}-Q_l
$$
Define the efficiency of a engine
$$
\eta=\frac{W}{Q_h}
$$
Ultize the processing equation of adiabats and isotherms
$$
\eta=1-\frac{T_l}{T_h}
$$
The refrigerator
$$
\epsilon=\frac{Q_l}{W}=\frac{T_l}{T_h-T_l}
$$

**Carnot's Theorem**:
Of all engine working between two given temperatures, none is more efficient than Carnot's engine.
**Corollary**:
All reversible engines have the same efficiency $1-\frac{T_l}{T_h}$
## 1.3 The Equivalence of the Three Laws
Carnot$\rightarrow$Calausius
![[卡诺定理1.jpg]]
Carnot$\rightarrow$Kelvin
![[卡诺定理2.png]]
## 1.4 Calausius' Theorem
For a Carnot cycle, exist
$$
\frac{Q_h}{Q_l}=\frac{T_h}{T_l}
$$
Define $\Delta Q_{\text{rev}}$ as the heat entering the system
$$
\sum\frac{\Delta Q_{\text{rev}}}{T}=\frac{Q_h}{T_h}-\frac{Q_l}{T_l}=0
$$
For an anbitrary reversible cycle, we can divide it into infinity Carnot cycle
$$
\oint\frac{\bar{\smash{d}}Q}{T}=0
$$
For a cycle contains irreversible process
![[克劳修斯定理.jpg]]
According to the second law
$$
W_{total}=\Delta W+\sum W_i\leq0
$$
or the total system will absorb heat for reservior $T$ and transform them to work completely.
$$
T\sum\frac{Q_i}{T_i}\leq0 
$$
$$
\Downarrow
$$
$$
\oint\frac{\bar{\smash{d}}Q}{T}\leq0
$$
**Calausius Theorem**:
$$
\oint\frac{\bar{\smash{d}}Q}{T}\leq0
$$
Equiality holds only for reversible cycle.
# 2.Entropy
## 2.1 Definition
For a reversible cycle $\oint\frac{\bar{\smash{d}}Q}{T}=0$, indicating that $\int_A^B\frac{\bar{\smash{d}}Q}{T}$ is path-independent. In terms of this, we can define a new state function.
$$
\Delta S=S(B)-S(A)=\int_A^B\frac{\bar{\smash{d}}Q}{T} |_{\text{reversible}}
$$
and
$$
\mathrm{d}S=\frac{\bar{\smash{d}}Q_{\text{rev}}}{T}
$$
An adiabatic process is isentropic.
## 2.2 Irreversible Process
For an irreversible process form $A$ to $B$ ,we can built a reversible process to connect them. According to Calausius theorem
$$
\oint\frac{\bar{\smash{d}}Q}{T}=\int_A^B\frac{\bar{\smash{d}}Q_{\text{irr}}}{T}+\int_B^A\frac{\bar{\smash{d}}Q_{\text{rev}}}{T}<0
$$
$$
\int_A^B\frac{\bar{\smash{d}}Q_{\text{irr}}}{T}<\int_A^B\frac{\bar{\smash{d}}Q_{\text{rev}}}{T}
$$
$$
\Delta S<\int_A^B\frac{\bar{\smash{d}}Q_{\text{irr}}}{T}
$$
Particularly, for a thermally isolated system, $\bar{\smash{d}}Q=0$, the inequiality becomes
$$
\Delta S\geq0
$$
## 2.3 Rewrite the First Law
The first law
$$
\mathrm{d}U=\bar{\smash{d}}Q+\bar{\smash{d}}W
$$
For reversible change
$$
\begin{align*}\bar{\smash{d}}Q&=T\mathrm{d}S\\\bar{\smash{d}}W&=-P\mathrm{d}V\end{align*}
$$
Conbine them
$$
\mathrm{d}U=T\mathrm{d}S-P\mathrm{d}V
$$
Since the quantities in the equation are all state functions, the formula holds for irreversible change too.

Take $S$ and $V$ as the natural varibles
$$
\mathrm{d}U=\left(\frac{\partial U}{\partial S}\right)_V\mathrm{d}S+\left(\frac{\partial U}{\partial V}\right)_S\mathrm{d}V
$$
Compare the two equation
$$
\begin{align*}T&=\left(\frac{\partial U}{\partial S}\right)_V\\P&=-\left(\frac{\partial U}{\partial V}\right)_S\end{align*}
$$
## 2.4 Free Expansion
Consider some ideal gas expand from $V_0$ to $2V_0$ in vaccum. This is a irreversible process, but it's intial  and final states are the same as isothermal process.
$$
T\mathrm{d}S=P\mathrm{d}V=\frac{nRT}{V}\mathrm{d}V
$$
$$
\mathrm{d}S=nR\frac{\mathrm{d}V}{V}
$$
$$
\Delta S=nR\int_{V_0}^{2V_0}\frac{\mathrm{d}V}{V}=nR\ln2
$$
## 2.5 The Statistical Basis for Entropy
Having konwn
$$
T=\left(\frac{\partial U}{\partial S}\right)_{V}
$$
or 
$$
\frac{1}{T}=\left(\frac{\partial S}{\partial U}\right)_V
$$
And the statistical definition of temperature
$$
\frac{1}{k_BT}=\frac{\mathrm{d}\ln\Omega}{\mathrm{d}E}
$$
Compare the two equations
$$
S=k_B\ln\Omega
$$
Attention, this formula defines the absolut entropy.

**To interpret free expansion**
Intially, all the molecules can only stay in one side and the $\Omega=1$, but finally each of the can stay in both side and $\Omega$ becomes to 2.
The number of the molecules in $n\cdot N_A$
$$
\begin{align*}\Delta S&=k_B\ln 2^{n\cdot N_A}-k_B\ln 1^{n\cdot N_A}\\&=nR\ln2\end{align*}
$$
