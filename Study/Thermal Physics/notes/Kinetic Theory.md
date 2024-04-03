# 1.The Maxwell-Boltzman Distribution
The distribution is appropriate for monatomic gas.
## 1.1 The Velocity Distribution
For monatomic gas, we only need to consider the kinetic energe.
$$E=\frac{1}{2}m(v_x^2+v_y^2+v_z^2)$$
Consider one direction as example, the distribution can be formulated as
$$g(v_x)=Ce^{-\frac{mv_x^2}{2k_BT}}$$
$C$ is the normalized constant
$$\int Ce^{-\frac{mv_x^2}{2k_BT}}\mathrm{d}v_x=1\Rightarrow C=\sqrt{\frac{m}{2\pi k_BT}}$$
So that, the complete distribution is
$$f(\vec{v})\mathrm{d}\vec{v}=\left(\frac{m}{2\pi k_BT}\right)^{\frac{3}{2}}e^{-\frac{m(v_x^2+v_y^2+v_z^2)}{2k_BT}}\mathrm{d}v_x\mathrm{d}v_y\mathrm{d}v_z$$
## 1.2 The Speed Distribution
Looking back to the velocity distribution, $\mathrm{d}v_x\mathrm{d}v_y\mathrm{d}v_z$ is acturally the volumu differential in the velocity phase space.
When we omit the direction and only the value of the velocity (speed), the differential becomes $4\pi v^2\mathrm{d}v$
Hence, the speed distribution is
$$f(v)\mathrm{d}v=4\pi v^2\left(\frac{m}{2\pi k_BT}\right)^{\frac{3}{2}}e^{-\frac{mv^2}{2k_BT}}\mathrm{d}v$$
From this idea, we can induce the speed distribution in Spherical coordinate
$$
\mathrm{d}P=\left(\frac{m}{2\pi k_BT}\right)^{\frac{3}{2}}e^{-\frac{mv^2}{2k_BT}}v^2\sin\theta\ \mathrm{d}v\ \mathrm{d}\theta\ \mathrm{d}\phi
$$
Some mean values
$$
\begin{align*}\overline{v}&=\sqrt{\frac{8k_BT}{\pi m}}\\\overline{v^2}&=\frac{3k_BT}{\pi m}\end{align*}
$$
Furthermove
$$
\overline{E_k}=\frac{1}{2}m\overline{v^2}=\frac{3}{2}k_BT
$$
## 1.3 Doppler Broadening
A atom with a component of velocity $v_x$ towards the detector will has Doppler shift $\omega_0(1+\frac{v_x}{c})$
The spectral line is determined by the formula
$$
I(\omega)\propto \exp(-\frac{mc^2(\omega_0-\omega)^2}{2k_BT\omega_0^2})
$$
$\Delta \omega$ repersent the full-width at half-maximum of this spectral line
$$
\frac{I(\omega_0+\frac{\Delta\omega}{2})}{I(\omega_0)}=\frac{1}{2}
$$
$$
\frac{\Delta \omega}{\omega_0}=2\sqrt{2\ln 2\frac{k_BT}{mc^2}}
$$
Another source of broadening arise from the molecular collision. Thus Doppler broadening is more significient in low-pressure gas.
# 2.The Applications
## 2.1 Pressure
If there is a symmetry in $\phi$, the speed distribution in coordinate becomes
$$
f(v)\mathrm{d}\tau=2\pi v^2\sin \theta\left(\frac{m}{2\pi k_BT}\right)^{\frac{3}{2}}e^{-\frac{mv^2}{2k_BT}}\mathrm{d}v\ \mathrm{d}\theta
$$
![[Pasted image 20240330111443.png]]
Given a fixed range $(\mathrm{d}t,\mathrm{d}S,\theta\sim\theta+\mathrm{d}\theta,v\sim v+\mathrm{d}v)$, the number of molecules that hit on the wall is
$$
\mathrm{d}N=v\cos\theta\mathrm{d}t\mathrm{d}S\cdot n\cdot2\pi v^2\sin \theta\left(\frac{m}{2\pi k_BT}\right)^{\frac{3}{2}}e^{-\frac{mv^2}{2k_BT}}\mathrm{d}v\ \mathrm{d}\theta
$$
The pressure on the wall by $\mathrm{d}N$ is 
$$
\frac{\mathrm{d}N\cdot 2v\cos\theta}{\mathrm{d}t\ \mathrm{d}S}=4\pi v^4\sin\theta\cos\theta\left(\frac{m}{2\pi k_BT}\right)^{\frac{3}{2}}e^{-\frac{mv^2}{2k_BT}}\mathrm{d}v\ \mathrm{d}\theta
$$
Intergate $v:0\sim\infty,\theta:0\sim\frac{\pi}{2}$, and the result is
$$
P=\frac{1}{3}nm\overline{v^2}=nk_BT
$$
Multiply $V$ on both side and it becomes the ideal gas equation
$$
PV=\nu RT
$$
The formula indicates that the pressure is independent of the mass of the molecules (since the molecules with bigger mass will have lower mean velocity)

The connection between pressuer and kinetic energe density
$$
P=\frac{2}{3}u
$$
\* Particularly, under exterme relativistic condition
$$
P=\frac{1}{3}u\quad(E\sim mv^2)
$$
## 2.2 Molecular Effusion
Effusion satisfy a expirical relation:Graham's Law
$$
\frac{\Gamma_A}{\Gamma_B}=\sqrt\frac{m_B}{m_A}
$$
where $\Gamma$ repersent the flux of the molecules.

**(1).Flux**
![[Pasted image 20240330113554.png]]
Utilize the formula we have get about the number of molecules that hit on the wall, the flux is
$$
\begin{align*}\Gamma&=\frac{\int\mathrm{d}N}{\mathrm{d}t}\\&=\iint2\pi v^3\sin\theta\cos\theta\left(\frac{m}{2\pi k_BT}\right)^{\frac{3}{2}}e^{-\frac{mv^2}{2k_BT}}\mathrm{d}v\ \mathrm{d}\theta\\&=\frac{1}{4}n\overline{v}\end{align*}
$$
Since $P=nk_BT$, the equation can transform to
$$
\begin{align*}\Gamma&=\frac{1}{4}\frac{P}{k_BT}\sqrt{\frac{8k_BT}{\pi m}}\\&=\frac{P}{\sqrt{2\pi k_BTm}}\end{align*}
$$
Indicate $\Gamma\propto\frac{1}{\sqrt{m}}$
(2).The speed-distribution of the molecules effused
$$
\begin{align*}f(v)&=\frac{\mathrm{d}N(v)}{N_{tot}}\\&=\frac{\int_{0}^{\frac{\pi}{2}}2\pi v^3\sin\theta\cos\theta\left(\frac{m}{2\pi k_BT}\right)^{\frac{3}{2}}e^{-\frac{mv^2}{2k_BT}}\mathrm{d}v\ \mathrm{d}\theta}{\Gamma}\\&=2\pi^2v^3\left(\frac{m}{2\pi k_BT}\right)^{2}e^{-\frac{mv^2}{2k_BT}}\end{align*}
$$
This is the Maxwell speed distribution in the forth-dimension.
And the mean kinetic energe $E_k=\frac{1}{2}m\overline{v^2}=2k_BT$
## 3.The Mean Free Path
**(1).The mean collision time**
Find the probability that the collision happens in $(t,t+\mathrm{d}t)$
$$
\begin{cases}\text{moving without collision}\quad(0,t)\\\text{collide}\quad(t,t+\mathrm{d}t)\end{cases}
$$
Consider a special condition that the molecule we concern is moving at speed $v$ and other molecules are stationary. Assume the collision cross-section of each molecule is $\sigma$ and the particle number density is $n$.
Therefore, the probability the molecule collide with others in $\mathrm{d}t$ is $n\sigma v\mathrm{d}t$.
Define $P(t)$ is the probability that the molecule dosen't collide with others in $(0,t)$. 
$$
\begin{align*}P(t+\mathrm{d}t)&=P(t)+\frac{\mathrm{d}P(t)}{\mathrm{d}t}\mathrm{d}t\\&=P(t)\cdot P(\mathrm{d}t)\\&=P(t)\cdot(1-n\sigma v\mathrm{d}t)\end{align*}
$$
Thus, we get the differential equation about $P$ and $t$
$$
\frac{\mathrm{d}P}{\mathrm{d}t}=-P\cdot n\sigma v
$$
And the solution is 
$$
P=e^{-n\sigma vt}
$$
Where $P(0)=1$
The probability that the molecule collide with another molecule in $(t,t+\mathrm{d}t)$ is
$$
\begin{align*}f(t)\mathrm{d}t&=P(t+\mathrm{d}t)-P(t)\\&=n\sigma v\cdot e^{-n\sigma vt}\mathrm{d}t\end{align*}
$$
Thus the mean collision time
$$
\tau=\int_0^\infty n\sigma vt\cdot e^{-n\sigma vt}\mathrm{d}t=\frac{1}{n\sigma v}
$$
**(2).The mean free path**
$$
\lambda=\overline{v}\tau
$$
When caluclating $\tau$, we assume all the molecules are stationary except the one we corcern, but acturally all of them are whizzing. So we should take the relative velocity as $v$.
$$
\vec{v}_r=\vec{v}_1-\vec{v}_2
$$
$$
|\vec{v}_r|^2=v_1^2+v_2^2-2\vec{v}_1\cdot\vec{v}_2
$$
$$
\overline{v_r}\approx\sqrt{\overline{v_r^2}}=\sqrt{2\overline{v^2}}\approx\sqrt{2}\overline{v}
$$
Therefore
$$
\lambda\approx\frac{1}{\sqrt{2}n\sigma}=\frac{k_BT}{\sqrt{2}P\sigma}
$$
**(3).Mixing gas**
Consider a mixing gas with two different kinds of particles, and the parameters are $(n_1,m_1)$ and $(n_2,m_2)$
Suppose $\sigma_1$ is the collision cross-section particle 1 to particle 1, $\sigma_2$ is that particle 2 to 2, and $\sigma_r$ is that of they to each other.
Consider particle 1, the probability it collide with other particle is
$$
(n_1v_{1-1}\sigma_1+n_2v_{1-2}\sigma_r)\mathrm{d}t
$$
Similarily we get the mean collision time
$$
\tau_1=\frac{1}{n_1v_{1-1}\sigma_1+n_2v_{1-2}\sigma_r}
$$
And
$$
\begin{cases}v_{1-1}\approx\sqrt{2}\overline{v_1}\\v_{1-2}=\sqrt{\overline{v_1^2}+\overline{v_2^2}}\end{cases}
$$
The mean free path
$$
\begin{align*}\lambda_1&=\overline{v_1}\tau=\frac{1}{\sqrt{2}n_1\sigma_1+n_2\sigma_r\sqrt{1+\frac{\overline{v_2^2}}{\overline{v_1^2}}}}\\&=\frac{1}{\sqrt{2}n_1\sigma_1+n_2\sigma_r\sqrt{1+\frac{m_1}{m_2}}}\end{align*}
$$
And $\lambda_2$ has the equal status to $\lambda_1$
$$
\lambda_2=\frac{1}{\sqrt{2}n_2\sigma_2+n_1\sigma_r\sqrt{1+\frac{m_2}{m_1}}}
$$
