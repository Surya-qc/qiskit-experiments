## **Quantum Interference — Mach-Zehnder Interferometer (MZI)**

###### **Qiskit simulation of quantum interference, phase control, and which-path detection**





#### **What is the MZI?**

###### 

###### The Mach-Zehnder Interferometer is one of the deepest experiments in quantum mechanics. It provides direct proof of superposition, the most fundamental quantum mechanical nature of particles.

###### When a single photon enters the MZI, it does not take one path or the other. It takes a superposition of both paths simultaneously and undergoes interference with itself. This is why every photon ends up fully at one detector while the other detector sees complete darkness — not because of any classical wave effect, but because of quantum interference of a single particle with itself.

###### This experiment also reveals a strange character of the photon: the photon appears to know the existence of a path it did not take. And when you try to find out which path it took, that knowledge destroys the interference completely — proving that for quantum particles, realism is not applicable.

###### 

###### 

#### **MZI in Qiskit**

###### 

###### In Qiskit, the MZI maps directly to quantum gates:

###### 

|**Real MZI**|**Qiskit**|
|-|-|
|Beam splitter 1|H gate|
|Path length difference|RZ(θ) gate|
|Beam splitter 2|H gate|
|Detector|Measurement|



#### 

#### **Notebooks**



##### **01 — MZI Basic**



###### Tests four phase values and shows how the detector outcome changes:



|**Phase (θ)**|**Result**|**Physical meaning**|
|-|-|-|
|0|{'0': 1000}|Constructive interference — all photons to D0|
|π/2|{'0': \~500, '1': \~500}|Partial interference|
|π|{'1': 1000}|Destructive interference — all photons to D1|





##### **02 — Phase Sweep**



###### Runs the MZI 50 times, sweeping θ continuously from 0 to 2π. Plots the full interference pattern showing how P(|1⟩) follows a smooth sine curve — controlled entirely by phase.





##### **03 — Which Path Experiment**



###### Places a measurement between the two beam splitters — equivalent to putting a detector on one path of the MZI. The moment which-path information is obtained, superposition collapses and interference is completely destroyed. Result goes from {'1': 1000} to a random \~25% distribution across all outcomes.





#### **Results**



##### **Basic MZI — No Phase vs π Phase**

###### 

* ###### No phase: all photons to D0
* ###### π phase: all photons to D1

###### 

###### 

##### **Phase Sweep — Interference Pattern**

###### 

###### Smooth sine curve from 0 to 2π showing continuous control of interference by phase.

###### 

###### 

##### **Which Path — Interference Destroyed**

###### 

###### Normal MZI (π phase): {'1': 1000}

###### Which path measurement: {'10': \~250, '01': \~250, '00': \~250, '11': \~250}

###### 

###### 

##### **How to Run**

###### 

###### *pip install qiskit qiskit-aer matplotlib numpy*

###### *jupyter notebook*

###### 

###### Open each notebook in order and run all cells.

###### 

###### 

##### **Tools**

###### 

* ###### Python 3
* ###### Qiskit
* ###### Qiskit Aer (local simulator)
* ###### NumPy
* ###### Matplotlib

###### 

###### 

##### **Author**

##### **Surya Surendran Nair**

##### MSc Physics | IIT Delhi Quantum Computing Certified | Qiskit Developer

##### https://github.com/SuryaJackson

