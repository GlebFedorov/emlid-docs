#Tuning LoRa settings for RTK data collection

##Overview

This guide explains how to tune LoRa radios on Reach base and rover for RTK.

!!! tip ""
	In [Base and Rover setup video guide](https://youtu.be/4GfUDoDwEAE) we show recommended settings for LoRa. These settings should work well in most cases so check this video first.

## LoRa setup

There are several factors that may affect the range of LoRa radios built in Reach RS/RS+ and Reach RS2:

* Environmental conditions
* Configuration in ReachView app
* Hardware setup in the field

Go through this simple check-list to make sure your setup is optimal:

* Check that LoRa antennas are firmly attached

* Make sure you specified the same LoRa settings in **Base mode** tab on the base unit and in **Correction Input** on the rover. Here are the recommended settings:
	- Frequency is set by default in the app
    - 20 dBm output power
    - 9.11 kb/s air data rate

??? "Base configuration"
    <div style="text-align: center;"><img src="../img/reach/tuning-lora/base-mode.png" style="width: 800px;"></div>

??? "Rover configuration"
    <div style="text-align: center;"><img src="../img/reach/tuning-lora/correction-input.png" style="width: 800px;"></div>

* Check the surroundings. In the line of sight, the baseline may reach up to 8 kilometers ([or sometimes even 19km](https://emlid.com/reach-rs-integrated-radio-hits-19-2-km-baseline/)) while in a densely vegetated area the range may reduce down to several hundred meters. Make sure there are no obstacles that can reduce the range

## Advanced tuning

To improve the LoRa range even further, use the suggestions below.

### Air data rate

High air data rate provides a more stable correction stream that allows transmitting a larger number of RTCM3 messages. Choosing lower values of air data rate on the contrary limits the RTCM3 messages number but may significantly increase the baseline.

!!! tip ""
    The lower the air rate, the longer the working distance will be.

* Check your RTCM3 messages selection in the **Base mode** tab on the base unit. In case you use GPS and GLONASS in RTK Settings, then the following messages should be enabled:

??? "Reach RS+ base"
    * 1002 (GPS L1 Observations), 1 Hz
    * 1006 (ARP station coordinate), 0.1Hz
    * 1010 (GLONASS L1 observation), 1 Hz
    
    <div style="text-align: center;"><img src="../img/reach/tuning-lora/rtcm-selection.png" style="width: 800px;"></div>

??? "Reach RS2 base"
    * 1006 (ARP station coordinate), 0.1 Hz
    * 1074 (GPS MSM4), 1 Hz
    * 1084 (GLONASS MSM4), 1 Hz

* Test the setup with lower air data rate values: 4.56 kb/s and then 2.6 kb/s

!!! note ""
    Make sure you changed the air data rate on both base and rover devices: 

    * In the **Base mode** tab on the base 
    * In the **Correction input** tab on the rover

### Frequency

Sometimes allowed frequency range in your working area can be affected by some local factors. That is why it is important to find a frequency that works efficiently for your environmental conditions.

* Check that you set up [the default settings for LoRa mentioned above](#lora-setup)

* Double check which frequency ranges can be used in your area

!!! danger ""
	Some frequency bands might not be allowed in your region. These limitations are currently applied automatically in ReachView for some countries.

* Set up frequency at the highest allowed value

!!! note ""
	Make sure you set up the same frequency on both base and rover devices:
    
    * In the **Base mode** tab on the base 
    * In the **Correction input** tab on the rover

* Check the maximum LoRa range you can get with that frequency. If the range is not sufficient, go down with the 1-2 MHz step until you find the frequency that works best for your area

<br>

If you still experience difficulties with tuning LoRa settings, don’t hesitate to contact us on support@emlid.com or create a thread on [Emlid community forum](https://community.emlid.com) with all your questions!