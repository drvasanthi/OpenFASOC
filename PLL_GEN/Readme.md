# PHASE LOCK LOOP (PLL) Generator

Phase Lock Loop (PLL) is a system that consists of three major parts; Phase Frequency Detector (PFD), Charge Pump and Loop Filter, and Voltage Controlled Oscillator (VCO). A PLL is highly preferred because it is a feedback system that compares the output frequency from the input frequency and can survive in a single chip. A PLL is normally used in well-timed clock generator, recovery of signal from noisy communication channel and high performance wireless with additional application in PLL’s parts

![image](https://user-images.githubusercontent.com/67214592/206756380-842bbf63-04fe-4953-b108-526d30bd91db.png)

## Charge Pump

The charge pump circuit is connected with loop filter and located within PFD and VCO. Charge pump is functioning as a converter for the logic states of the PFD into an analog signal in order to control the VCO. The frequency of the VCO is controlled by the output signal of the charge pump circuit. The output voltage of the charge pump circuit must be held at a constant voltage, when PLL locks in some frequency. The charge pump consists of two switched current source that pump charge in or out of the
loop filter according to two logical inputs.

![image](https://user-images.githubusercontent.com/67214592/206757063-8215a48a-a4a5-4808-b97a-8849f9dc70ec.png)

Phase frequency detector

![image](https://user-images.githubusercontent.com/67214592/206757319-6b3cb1d2-fd15-4acc-a5ce-63b1006d24cb.png)

Frequency Divider

![image](https://user-images.githubusercontent.com/67214592/206757719-d345a6ab-2cea-4067-8686-9567aaa17b7d.png)

## VCO

Loop Filter circuit is also important to the performance of the PLL because it removes high frequency noise of the detector, influences the hold and captures ranges, and influences the switching speed of the loop in lock. Loop filter convert the output signal of phase frequency detector to control voltage and reduce the ripple from the charge pump. A charge pump circuit along with low pass filter is used to minimize the disturbances at the input of current-starved voltage controlled oscillator (CS-VCO) and to get a sharper and smoother signal at the CS-VCO output.

![image](https://user-images.githubusercontent.com/67214592/206757480-b9c40375-e9ff-4193-9397-d47f3af6bf7b.png)

Step 1: Import CP.sp file -> generates -> gds and lef files

![image](https://user-images.githubusercontent.com/67214592/206757975-53ae6b84-ff1f-4cb0-a606-ea96062aa587.png)

![image](https://user-images.githubusercontent.com/67214592/206758076-0125dc84-2866-45c8-b088-8531afb73c98.png)

Step 2: Layout View

![image](https://user-images.githubusercontent.com/67214592/206759424-9658e69e-bd50-4757-9561-2c954760e4e4.png)

![image](https://user-images.githubusercontent.com/67214592/206759064-fb5769bb-5b2e-43f4-a331-361ce790c4e4.png)

![image](https://user-images.githubusercontent.com/67214592/206759351-ad0a2b41-087d-4958-ba81-3ce07206561c.png)

# FUTURE WORK

1. Pre-layout simulation is not matching with Post-layout simulation.  
2. ALIGN PDK are been used in the design, this encounters an issue at OpenFasoc.

## Acknowledgement
  
  * Kunal Ghosh, Director, VSD Corp. Pvt. Ltd.
  * Nickson Jose, VLSI Engineer, VSD Corp. Pvt. Ltd.
  * Madhav Rao, Professor, IIIT-Bangalore.
  * Nanditha Rao, Professor, IIIT-Bangalore.

## Contact Information

  * Vasanthi D R, PhD Scholar, International Institute of Information Technology, Bangalore vasanthidr11@gmail.com
  * Kunal Ghosh, Director, VSD Corp. Pvt. Ltd. kunalghosh@gmail.com
  * Madhav Rao, Professor, IIIT-Bangalore. mr@iiitb.ac.in
  * Nanditha Rao, Professor, IIIT-Bangalore. nanditha.rao@iiitb.ac.in
  





