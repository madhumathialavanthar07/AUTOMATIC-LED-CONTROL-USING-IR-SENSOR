# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
    <img width="1919" height="1199" alt="p1" src="https://github.com/user-attachments/assets/767081cd-fd33-43b1-9b23-ecdfbd5c35cc" />


2. Click **File → New STM32 Project**.
     <img width="1918" height="1198" alt="p2" src="https://github.com/user attachments/assets/0917a441-c53b-4ab4-96ff-c567b2a4cb9c" />
      <img width="1920" height="1200" alt="p22" src="https://github.com/user-attachments/assets/4e4dc069-0e68-45b5-be0e-c7c79f137e4c" />


3. Select the **target microcontroller** or board and click **Next**.
      <img width="1919" height="1199" alt="m3" src="https://github.com/user-attachments/assets/91f29af0-894b-4c67-a6c4-69906ee6d647" />
  
4. Name the project.

   <img width="586" height="654" alt="m4" src="https://github.com/user-attachments/assets/a8a610b9-d271-4756-9d9e-8ca0983a36d0" />
  

5. The corresponding `.ioc` file will be generated automatically.
      <img width="1704" height="1023" alt="m5" src="https://github.com/user-attachments/assets/09be235e-8b1a-4dbd-ae3f-62506d3b9bbe" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
       <img width="1702" height="1017" alt="m6" src="https://github.com/user-attachments/assets/527e7190-8323-4806-89de-af5d30b56dd5" />
       <img width="1706" height="1016" alt="m66" src="https://github.com/user-attachments/assets/dca98816-3d6a-41da-82e9-1969dee0cf02" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
        <img width="1706" height="1025" alt="m7" src="https://github.com/user-attachments/assets/cb37918b-c44d-4129-9bdb-83277cafbfe2" />

8. Edit the generated main program as required.
   <img width="1919" height="1199" alt="m8" src="https://github.com/user-attachments/assets/914e4e5c-0563-48f4-b9d1-41a05d9ec6f2" />
    <img width="1919" height="1199" alt="m88" src="https://github.com/user-attachments/assets/08843c4a-f997-4986-b1f7-e2583445619d" />

9. Click **Project → Build All**.
     <img width="958" height="242" alt="m9" src="https://github.com/user-attachments/assets/184bd3a0-8981-4dee-ad87-846cd35e9e36" />

10. Link the **HEX file** using the post-build process.
    <img width="1919" height="1199" alt="m10" src="https://github.com/user-attachments/assets/c569a78e-193c-499a-9cfd-059b80dcdc51" />
  
11. Click **Debug** and connect the **STM Nucleo Board**.
     <img width="1914" height="1199" alt="m11" src="https://github.com/user-attachments/assets/467d4f8c-dc10-4a21-8d65-18a6fff63945" />

13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

<img width="603" height="432" alt="led on" src="https://github.com/user-attachments/assets/fc691c39-674e-4295-b13f-58a5f8c4782a" />
 

CASE 2: LED OFF

<img width="596" height="416" alt="led off" src="https://github.com/user-attachments/assets/0d53641f-21b0-44ba-9062-b6fc40c13e39" />

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




