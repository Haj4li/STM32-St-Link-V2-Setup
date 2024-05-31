# STM32-St-Link-V2-Setup
STM32 St Link V2 Setup (Blue Pill STM32F103C8T6)

Hello! this is a simple way to setup ST Link/V2 for a blue pill board (or anything else)

St Link V2:
![StLinkV2Image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/30d26258-2e71-4fc8-a434-a0225fc6074b)


Required tools and softwares:
  + ST Link usb driver [Download](https://files.waveshare.com/upload/a/a4/St-link_v2_usbdriver.zip)
  + STSW-LINK009 [Download](https://www.st.com/en/development-tools/stsw-link009.html)
  + STM32 ST-LINK utility [Download1](https://files.waveshare.com/upload/a/a2/STM32-ST-LINK-Utility.zip) [Download2](https://www.st.com/en/development-tools/stsw-link004.html)
  + Keil uVision (IDE) [Download](https://www.keil.com)
  + STM32CubeMX [Download](https://www.st.com/en/development-tools/stm32cubemx.html)

After you done setup required tools, now you need to connect the ST Link/V2 to the computer and then update firmware.
So open the ST-LINK utility software and from ST-Link->Firmware update:

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/b5061c23-318f-4d5b-8d05-b29263e76d5f)

If you have installed the drivers after clicking on Device Connect it should detect the hardware, if it's your first time connecting the ST-Link to your computer you have to update firmware (Just Click on Yes)

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/1f52c376-955a-47f4-9641-51f9241635ff)

If it's not your first time or got any error like this 

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/41b981f9-5ca3-46ee-90b3-2e3e7b172d77)

Click on OK and reconnect the device then try Device Connect if that didn't fix the issue check driver installations.

Now everything is ready for connecting the Blue Pill board to the St-Link/V2
Let's take a look on Blue Pill pinout [Source](https://deepbluembedded.com/stm32-blue-pill-pinout-programming-guide/):

![Bluepillpinout](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/186d171e-1327-409a-8588-e9218d19f4f3)

And here's the pinout for St-Link

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/edd9d453-dec0-47fc-a145-cc9fc14e1cb6)

What we do need are only this pins

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/6e3789f8-5c0d-4276-93c5-0866c56a31d6)

So we need 6 jumper wires and connect each pins like this image (sorry for bad drawing hope you manage the do the wiring)

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/656bd86d-e04d-4edd-abcd-97fad86e8d4e)
