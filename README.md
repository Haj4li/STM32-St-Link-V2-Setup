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

After wiring you should see the Blue Pill blue led blinking (it it's the first time) and red led is on, now go back to the ST-Link Utility and from Target->Setting

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/edad7be8-2835-4ec2-8677-39a3ab872899)

Make sure the target setting are the same as here

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/74c512b6-5408-4dc1-ac54-28014a040bf7)

Then click ok and we are ready to connect to microcontroller, first click on disconnect button and then connect 

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/39e47793-fa9e-4bb3-a03c-2348f8e44e65)

If you have done everything as i said the software should connect to your board and you can see the memory of it, if there's any kind of errors for connecting recheck the wiring and target setting if the error persist check them again 

Now click on the eraser button to erase the board memory 

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/75a41f34-4ad3-43cc-bfc9-ff550bf91e3f)

After this the blue led must stop blinking and you are ready to change the world!

You can upload your hex file to the board from File->Open

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/5998c755-88e4-46c7-8599-91404c7b883a)

Now find and select your hex file

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/56f19cf6-81ec-4e93-89e6-d21d84854a6b)

To upload it to the board click on Program Verify botton

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/1359d48e-9a09-450a-951a-3387906e06ce)

Now just click on start and wait 

![image](https://github.com/Haj4li/STM32-St-Link-V2-Setup/assets/48994331/ce7fc7f1-6a0b-4261-82d9-f98fbf788940)

After the uploading finished the board will be disconnected from the software so don't panic you can connect it again.

Here's my hex file for blinking LED on pin B9

[Blue Pill Pin B9 Blinking](https://github.com/Haj4li/STM32-St-Link-V2-Setup/blob/main/stlinksetup_blinkB9.hex)

And here's the code for Keil

```c
#include "stm32f1xx_hal.h"
GPIO_InitTypeDef GPIO_InitStruct;
int main(void)
{
  // Initialize the HAL library
  HAL_Init();

  // Enable the clock for the GPIO port B
  __HAL_RCC_GPIOB_CLK_ENABLE();
  // Configure the GPIO pin for PB9
  GPIO_InitStruct.Pin = GPIO_PIN_9;
  GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
  HAL_GPIO_Init(GPIOB, &GPIO_InitStruct);
  while (1)
  {
    // Turn on PB9
    HAL_GPIO_WritePin(GPIOB, GPIO_PIN_9, GPIO_PIN_SET);
    HAL_Delay(500);

    // Turn off PB9
    HAL_GPIO_WritePin(GPIOB, GPIO_PIN_9, GPIO_PIN_RESET);
    HAL_Delay(500);
  }
}
```

My Telegram Username: @CodePerson

