# What is GhostTouchAttack? ![](https://img.shields.io/badge/License-USSLab-blue)

Capacitive touchscreens have become the primary human-machine interface for personal devices such as smartphones and tablets. 
We present GhostTouchAttack, the first active contactless attack against capacitive touchscreens. GhostTouchAttack uses electromagnetic interference (EMI) to inject fake touch points into a touchscreen without the need to physically touch it.
By tuning the parameters of the electromagnetic signal and adjusting the antenna, we can inject two types of basic touch events, taps and swipes, into targeted locations of the touchscreen and control them to manipulate the underlying device.
We successfully launch the GhostTouchAttack on nine smartphone models. We can inject targeted taps continuously with a standard deviation of as low as 14.6 $\times$ 19.2 pixels from the target area, delay of less than 0.5s and a distance of up to 40mm. We show the real-world impact of the GhostTouchAttack in a few proof-of-concept scenarios, including answering an eavesdropping phone call, pressing the button, swiping up to unlock, and entering a password.

## How does GhostTouchAttack work?

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="./images/attack.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;"></div>
</center>

<!-- <img src=./images/attack.png width="795px"/> -->

# Background

A capacitive touchscreen is an input device normally layered on top of the display that detects human touches based on the capacitance variation. 
When a finger touches the screen, the capacitance at the touch point changes significantly as the charge stored in the screen gets drawn to the finger. By monitoring the capacitance variation at each point of the screen, a touchscreen can detect touch points and report touch events, e.g., tap, swipe, based on the timing and the locations of the detected touch points. 

The touch sensor consists of a grid of transmitting (TX) and receiving (RX) electrodes made of transparent conductive materials, e.g., indium-tin-oxide (ITO). The scan driving method is designed to locate the touch points on the screen by exciting all TX electrodes in turn. As only one TX is excited at a time, the touchscreen can locate a touch to a specific position by the row and column of the active TX-RX pair and can also support multi-touch detection. 

<img src=./images/mutual_cap.png height="150px"/> <img src=./images/sdm.png height="150px"/> 

# GhostTouch System Evaluation

## Implementation
The GhostTouch system consists of two parts, a touch injector and a phone locator. The touch injector can inject touch events, e.g., a tap, a swipe, or multi-touch, into the touchscreen, and it includes a signal generator, an amplifier, an on/off switch, and a receiving antenna array. The on/off switch is used to select the correct antennas to emit the EMI signals such that it can inject touch events into the targeted RX lines. The phone locator can identify the position of the touchscreen. It consists of a sensing antenna array, a data acquisition device, and a location calculator.

<img src=./images/GhostTouch_system.png height="200px"/>

<img src=./images/system_setup.png height="200px"/>

## Touch Injection

The following figure illustrates a comparison of the similarity between the taps from 30 volunteers and the ones injected by the attacker. Compared with real touch events, the taps injected by the attacker are distributed in a smaller range on the x-axis, and distributed in a larger range on the y-axis.

<img src=./images/similarity_xy_axis.png width="300px"/>

We evaluate the GhostTouchAttack on 11 phone models. We set the attack distance to 6mm for all phones for comparison. Broadly distributed touch points can be injected into 9 of these smartphones. According to the results, we can inject touch points at chosen positions for 6 out of 11 phone models with GhostTouchAttack. For Galaxy S20 FE 5G and iPhone SE (2020), our approach can inject touch points successfully and perform malicious operations, but not always with high precision. Such a vulnerability is still dangerous, to illustrate, we managed to establish a malicious Bluetooth connection on iPhone SE (2020), with an average delay of 7.1 seconds.

<img src=./images/phone_model.png width="500px"/>

## Phone Locator

The phone locator consists of sensing antennas and a NI MyDAQ. In practice we can place a matrix of sensing antennas to locate the phone positions with the following observation: a sensing antenna over the touchscreen can detect the radiated signals (e.g., the leaked signals of the TX excitation signal of the touchscreen at a frequency of 120Hz), while the ones away from the touchscreen will detect a weaker signal or none at all due to attenuation. Thus, the sensing antennas are used to receive the leaked signals, which are processed by the NI MyDAQ to deduce the phone location and orientation, with respect to the sensing antennas. After obtaining the phone position, we can infer the positions of the buttons based on the operating system and target application, e.g., Bluetooth connection accept dialog.

## Video Demos

Here are **video demos** showing the real-world impact of the GhostTouchAttack.

- Answer the phone call

<img src=./demo/accept_call.gif width="500px" />

<!-- 2. Attack at a distance of 40mm

<img src=./demo/attack40mm.gif width="500px" /> -->

- Connect the malicious Bluetooth

<img src=./demo/bluetooth.gif width="500px" />




# Citation

```

```


# Contact
* Prof. Wenyuan Xu (<wyxu@zju.edu.cn>)
* Prof. Xiaoyu Ji (<xji@zju.edu.cn>)

# Powered by

<table bgcolor="white">
<tr valign="middle">
<td width="50%" align="center" colspan="2">
 <a href="http://usslab.org">Ubiquitous System Security Laboratory (USSLab) 
</td>
<td width="50%" align="center" colspan="2">
  <a href="http://www.zju.edu.cn/english">Zhejiang University 
</td>
</tr>
<tr valign="middle">
<td width="50%" align="center" colspan="2">
  <a href="http://usslab.org"></a>
  <a href="http://usslab.org"><img 
src="./images/usslab_logo.png" height="80"></a>
</td>
<td width="50%" align="center" colspan="2">
  <a href="http://www.zju.edu.cn/english/"></a>
  <a href="http://www.zju.edu.cn/english/"><img 
src="./images/zju_logo.png" height="80"></a>
</td>
</tr>
</table>
