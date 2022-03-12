/**
 * @file main.c
 * @author Group 53
 * @brief This projects demonstrates Remote keyless Entry with STM32 as microcontroller and is working as a unidirectional system 
 * @version 0.1
 * @date 2022-03-11
 * 
 * @copyright Copyright (c) 2022
 * 
 */
#include <stdio.h>
#include "MyStm32f407xx.h"
#include<stdbool.h>


#define BTN_PRESSED ENABLE
/**
 * @brief This function runs successfully if encrypt is true
 * 
 * @return flag 
 */
int encrypt() // function made by K Mohammad Habeeb 

{ 
   bool flag = false;
   const int a = 143;
   const int b = 328;
   int result = a * b; // algorithm for encryption
   if(result==46904)
   {

      flag= true;
   }
   else{

      flag=false;
   }

   return flag;
}
   /**
    * @brief The delay function is declared for configuring the STM32 push button
    * 
    */
   void delay(void)
   {
      for (uint32_t i = 0; i < 5000000; i++);
   }
   /**
    * @brief Here we have made a function for alarm status, where all the LEDs are in off condition
    * 
    */
   void unlock (void)    
   {
      GPIO_WriteToOutputPin(GPIOD, GPIO_PIN_NO_11, 0); // Green LED
      GPIO_WriteToOutputPin(GPIOD, GPIO_PIN_NO_12, 0); // Orange LED
      GPIO_WriteToOutputPin(GPIOD, GPIO_PIN_NO_13, 0); // Red LED
      GPIO_WriteToOutputPin(GPIOD, GPIO_PIN_NO_14, 0); // Blue LED

   }
   /**
    * @brief Here we have made a function for window, where all the LEDs are in on condition
    * 
    */
   void lock (void)    
   {
      GPIO_WriteToOutputPin(GPIOD, GPIO_PIN_NO_11, 1);  // Green LED
      GPIO_WriteToOutputPin(GPIOD, GPIO_PIN_NO_12, 1);  // Orange LED
      GPIO_WriteToOutputPin(GPIOD, GPIO_PIN_NO_13, 1);  // Red LED
      GPIO_WriteToOutputPin(GPIOD, GPIO_PIN_NO_14, 1);   // Blue LED

   }
   /**
    * @brief Here we have made a function for car battery info, where all the LEDs are turned ON in clockwise sequence
    * 
    */
   void alarm_activation_deactivation(void) // The logic for this function was given by Tanmay 
   {
      delay();
      GPIO_ToggleOutputPin(GPIOD, GPIO_PIN_NO_11); // Green LED
      delay();
      GPIO_ToggleOutputPin(GPIOD, GPIO_PIN_NO_12); // Orange LED
      delay();
      GPIO_ToggleOutputPin(GPIOD, GPIO_PIN_NO_13);  // RED LED
      delay();
      GPIO_ToggleOutputPin(GPIOD, GPIO_PIN_NO_14);  // Blue LED
      delay();

   }
   /**
    * @brief Here we have made a function for door status, where all the LEDs are turned ON in anti-clockwise sequence
    * 
    */
   void Approach_Light(void) 
   {
      delay();
      GPIO_ToggleOutputPin(GPIOD, GPIO_PIN_NO_14); // Blue LED
      delay();
      GPIO_ToggleOutputPin(GPIOD, GPIO_PIN_NO_13); // Red LED
      delay();
      GPIO_ToggleOutputPin(GPIOD, GPIO_PIN_NO_12); // Orange LED
      delay();
      GPIO_ToggleOutputPin(GPIOD, GPIO_PIN_NO_11);  // Green LED
      delay();
      
   }
   int main(void)
   {   
      int count = 0;
      GPIO_Handle_t GpioLed, GPIOBtn, GpioLed1, GpioLed2, GpioLed3;

      GpioLed.pGPIOx = GPIOD;                                    
      GpioLed.GPIO_PinConfig.GPIO_PinNumber = GPIO_PIN_NO_11;     // PIN D11 is Green LED
      GpioLed.GPIO_PinConfig.GPIO_PinMode = GPIO_MODE_OUT;
      GpioLed.GPIO_PinConfig.GPIO_PinSpeed = GPIO_SPEED_FAST;
      GpioLed.GPIO_PinConfig.GPIO_PinOPType = GPIO_OP_TYPE_PP;
      GPIO_PeriClockControl(GPIOD, ENABLE);
      GPIO_Init(&GpioLed);

      GpioLed1.pGPIOx = GPIOD;
      GpioLed1.GPIO_PinConfig.GPIO_PinNumber = GPIO_PIN_NO_12;      // PIN D12 is Orange LED
      GpioLed1.GPIO_PinConfig.GPIO_PinMode = GPIO_MODE_OUT;
      GpioLed1.GPIO_PinConfig.GPIO_PinSpeed = GPIO_SPEED_FAST;
      GpioLed1.GPIO_PinConfig.GPIO_PinOPType = GPIO_OP_TYPE_PP;
      GPIO_PeriClockControl(GPIOD, ENABLE);
      GPIO_Init(&GpioLed1);

      GpioLed2.pGPIOx = GPIOD;
      GpioLed2.GPIO_PinConfig.GPIO_PinNumber = GPIO_PIN_NO_13;      // PIN D13 is Red LED
      GpioLed2.GPIO_PinConfig.GPIO_PinMode = GPIO_MODE_OUT;
      GpioLed2.GPIO_PinConfig.GPIO_PinSpeed = GPIO_SPEED_FAST;
      GpioLed2.GPIO_PinConfig.GPIO_PinOPType = GPIO_OP_TYPE_PP;
      GPIO_PeriClockControl(GPIOD, ENABLE);
      GPIO_Init(&GpioLed2);

      GpioLed3.pGPIOx = GPIOD;
      GpioLed3.GPIO_PinConfig.GPIO_PinNumber = GPIO_PIN_NO_14;     // PIN D14 is Blue LED
      GpioLed3.GPIO_PinConfig.GPIO_PinMode = GPIO_MODE_OUT;       
      GpioLed3.GPIO_PinConfig.GPIO_PinSpeed = GPIO_SPEED_FAST;
      GpioLed3.GPIO_PinConfig.GPIO_PinOPType = GPIO_OP_TYPE_PP;
      GPIO_PeriClockControl(GPIOD, ENABLE);
      GPIO_Init(&GpioLed3);

      GPIOBtn.pGPIOx = GPIOA;
      GPIOBtn.GPIO_PinConfig.GPIO_PinNumber = GPIO_PIN_NO_0;    // PIN A0 is Blue Switch
      GPIOBtn.GPIO_PinConfig.GPIO_PinMode = GPIO_MODE_IN;
      GPIOBtn.GPIO_PinConfig.GPIO_PinSpeed = GPIO_SPEED_FAST;
      GPIOBtn.GPIO_PinConfig.GPIO_PinPuPdControl = GPIO_NO_PUPD;
      GPIO_PeriClockControl(GPIOA, ENABLE);
      GPIO_Init(&GPIOBtn);
      
      if (encrypt())
      {

         while (1)
         {
            if (GPIO_ReadFromInputPin(GPIOA, GPIO_PIN_NO_0) == BTN_PRESSED)  
               delay();
               count = count + 1;    // count is incremented when push button is pressed by the user
            }
            if (count == 3)  
            {
               lock();
            }
            else if (count == 9)
            {
                unlock();
            }
            else if (count==18)
            {

               alarm_activation_deactivation();
            }
            else if (count==27)
            {
               Approach_Light();
            }
         }
      }
   }

