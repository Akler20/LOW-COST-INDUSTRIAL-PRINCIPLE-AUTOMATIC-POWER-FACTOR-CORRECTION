# LOW-COST-INDUSTRIAL-PRINCIPLE-AUTOMATIC-POWER-FACTOR-CORRECTION
1 System Description
The system is organized into four major functional blocks: sensing, signal processing,
decision making, and correction. In the sensing stage, the ZMPT101B measures the AC
voltage waveform while the SCT-013 measures the load current. In the signal processing
stage, the Arduino samples both waveforms, removes offsets, applies calibration factors,
and computes electrical parameters such as Vrms, Irms, real power, apparent power,
reactive power, and power factor.
In the decision-making stage, the controller compares the measured power factor with
a predefined target value such as 0.95 lagging. Based on the difference, it estimates the
reactive power that must be supplied by the capacitor bank. In the correction stage, the
relay module switches one or more capacitor steps to inject leading reactive power and
improve the overall system power factor.
9 Working
The system starts by initializing the Arduino, sensor interfaces, and relay outputs. Once
the inductive load is connected, the voltage and current sensors begin providing analog
signals proportional to the mains voltage and load current.
The Arduino continuously samples both signals over multiple AC cycles. Each pair
of voltage and current samples is used to calculate instantaneous power. After collecting
enough samples, the firmware calculates average real power, RMS voltage, RMS current,
and apparent power. The true power factor is then determined using PF = P/S.
If the measured power factor is lower than the desired value, the controller calculates
the reactive power of the load and then determines the capacitor reactive power required
for correction. Based on this value, a suitable combination of capacitor steps is selected.
The relay module energizes the corresponding channels and connects the capacitor bank
to the circuit. This reduces lagging reactive power, improves the power factor, and lowers
2
the line current. The process repeats continuously so that the system adapts to changes
in the load.
3 Mathematical Formulation
The mathematical formulation used in this project is summarized below:
Instantaneous Power
Average Real Power
RMS Voltage
RMS Current
Apparent Power
True Power Factor
Reactive Power
p(t) = v(t)i(t)
P = 1
N 
N
k=1 
vkik
N
Vrms =
1
N
k=1
v2
k
N
Irms =
1
N
k=1
S =Vrms ·Irms
PF = P
S
i2
k
Q=Ptan cos−1(PF)
Required Capacitive Compensation
Qc =P(tanϕ1 −tanϕ2)
(1)
(2)
(3)
(4)
(5)
(6)
(7)
(8)
10
4 Applications
• Industrial power systems
• Energy monitoring
• Educational laboratories
• Smart distribution panel
