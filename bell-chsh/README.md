## Bell Inequality \& CHSH Test — Qiskit Simulation



This is a Qiskit simulation of entangled qubit measurement, that reproduces the result of Aspect's 1982 experiment. Aspect's 1982 experiment shows that quantum entangled particles violate the CHSH inequality, ruling out local realism.

In our simulation we are preparing maximally entangled Bell state |Φ⁺⟩ = (|00⟩ + |11⟩)/√2. And we create a polarizer like rotation in our simulation then measurement in z basis, and computes the CHSH correlation parameter s.



Our simulation results in **S ≈ 2.76**, which violates the classical bound and approaches the Tsirelson bound, which **2√2 ≈ 2.828**. This result consistent with quantum mechanical prediction, and rules out local hidden variable theories as as an explanation for the observed correlations. 



The sign convention follows the standard CHSH form: 



&#x09;	**S = E(a,b) − E(a,b′) + E(a′,b) + E(a′,b′)**



The minus sign on E(a,b′) is intentional and determines which angle configuration maximises S. With the angles chosen here, the theoretical maximum is 2√2. 



###### **Theory: CHSH inequality**



For any local hidden-variable theory, the CHSH inequality states:



**|S| = |E(a,b) − E(a,b′) + E(a′,b) + E(a′,b′)| ≤ 2**



where **E(θ₁, θ₂)** is the correlation between measurements at angles **θ₁** and **θ₂**. Quantum mechanics predicts:



**E(θ₁, θ₂) = cos(2(θ₁ − θ₂))**



The maximum quantum violation is the **Tsirelson bound**:



**|S|\_max = 2√2 ≈ 2.828**



Achieved at angle separations of **22.5°,** the configuration used here.



###### **Circuit design**

**q0: ──H──●──RY(−2θ₁)──M──**

&#x20;          **│**

**q1: ─────CX──RY(−2θ₂)──M──**    



The two-qubit circuit prepares the Bell state **|Φ⁺⟩** then applies independent measurement-basis rotations. The correlation is computed as:



**E = (N₀₀ + N₁₁ − N₀₁ − N₁₀) / N\_shots**



where **N\_xy** denotes the count of outcome **|xy⟩** across all shots. This is equivalent to computing **⟨Z⊗Z⟩** in the rotated basis.

The RY rotation angle is **−2θ**, not **−θ**. The factor of **2** arises because **RY** rotates the Bloch sphere by twice the argument. Omitting this factor produces incorrect correlations and a deflated **S** value.



###### **Results**



|Quantum S (simulated)|Classical bound|Tsirelson bound|
|-|-|-|
|≈ 2.76|2.00|2√2 ≈ 2.828|



###### **Correlation table**



|Angle pair|θ₁ (°)|θ₂ (°)|E (simulated)|E (theory)|
|-|-|-|-|-|
|E(a, b)|0|22.5|+0.707|+0.707|
|E(a, b')|0|67.5|-0.707|-0.707|
|E(a', b)|45|22.5|+0.707|+0.707|
|E(a', b')|45|67.5|+0.707|+0.707<br />|

|S = E(a, b) − E(a, b′) + E(a′, b) + E(a′, b′)                  ≈ 2.76–2.83           2.828|
|-|



Simulated values vary slightly per run due to shot noise (shots = 1000). Set **seed\_simulator=42** for reproducibility.



What struck me running this was how close the simulated S value gets to the Tsirelson bound even at 1000 shots — the cosine structure is remarkably stable across the full angular sweep.





###### **Correlation vs. angle difference**



The second part of the script sweeps θ₂ from −90° to 90° with θ₁ = 0° and plots E against **Δθ = θ₂ − θ₁**. The expected cosine curve confirms the simulator matches theory across the full angular range.



##### **How to run**

###### **Installation**



###### pip install qiskit qiskit-aer matplotlib numpy



###### **Running**



###### python bell\_chsh.py

###### 



When prompted, enter measurement angles in degrees (e.g. 0 and 22.5) for the single-pair correlation measurement. The CHSH sweep and angle-correlation plot run automatically thereafter.



###### **Expected terminal output**



Enter Theta 1 in degree: **0**

Enter Theta 2 in degree: **22.5**

Value of E=  **0.7120**

Theoretical E = **0.7071**



Value of E= **0.6980**

Value of E= **-0.7020**

Value of E= **0.6940**

Value of E= **0.7140**

CHSH S = **2.8040**

Classical bound: **2.0000**

Tsirelson bound: **2.8284**



###### **References**



\- Aspect et al., Phys. Rev. Lett. 49, 1804 (1982)

\- Clauser, Horne, Shimony, Holt, Phys. Rev. Lett. 23, 880 (1969)

\- Qiskit documentation: https://docs.quantum.ibm.com





