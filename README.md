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
   <img width="1907" height="1068" alt="Screenshot 2025-11-11 110752" src="https://github.com/user-attachments/assets/ccda8b45-7c20-48f1-a459-53ac3cfda719" />


2. Click **File → New STM32 Project**.
  <img width="1900" height="1067" alt="Screenshot 2025-11-11 111056" src="https://github.com/user-attachments/assets/d82ae604-f86a-4ceb-913f-fe7a32bb22d0" />
<img width="1907" height="1068" alt="Screenshot 2025-11-11 111114" src="https://github.com/user-attachments/assets/2cbaab37-10f7-439b-9b4f-2a288a594a9b" />


3. Select the **target microcontroller** or board and click **Next**.
  <img width="1907" height="1068" alt="Screenshot 2025-11-11 111114" src="https://github.com/user-attachments/assets/2cbaab37-10f7-439b-9b4f-2a288a594a9b" />



4. Name the project.
   <img width="1907" height="1068" alt="Screenshot 2025-11-11 111228" src="https://github.com/user-attachments/assets/a4ee4ad7-c13c-4dc7-8b89-33343de6e547" />


5. The corresponding `.ioc` file will be generated automatically.
  <img width="1920" height="1080" alt="Screenshot 2025-11-11 114821" src="https://github.com/user-attachments/assets/3a6a3e99-5352-4722-a320-ab4c64022d78" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  <img width="1920" height="1080" alt="Screenshot 2025-11-11 114747" src="https://github.com/user-attachments/assets/61cc17cb-2090-4cb9-8ab2-4ff71025f0af" />

<img width="1920" height="1080" alt="Screenshot 2025-11-11 115648" src="https://github.com/user-attachments/assets/b5567c8b-dc93-43cc-af84-b3b607fc87c7" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
 <img width="1920" height="1080" alt="Screenshot 2025-11-11 115756" src="https://github.com/user-attachments/assets/5de8f218-f3ad-4fd1-b5be-429e13926634" />

 
8. Edit the generated main program as required.
  <img width="1920" height="1080" alt="Screenshot 2025-11-11 114901" src="https://github.com/user-attachments/assets/3f68943d-27cb-48e0-b450-041384442c23" />

9. Click **Project → Build All**.
    <img width="1920" height="1080" alt="Screenshot 2025-11-11 115001" src="https://github.com/user-attachments/assets/ca2bf9e1-69a4-4771-818d-0b779e89ab5b" />


10. Link the **HEX file** using the post-build process.
   <img width="1920" height="1080" alt="Screenshot 2025-11-11 115026" src="https://github.com/user-attachments/assets/180c4f9f-0fa0-4d96-8659-548aecc9a04c" />


11. Click **Debug** and connect the **STM Nucleo Board**.
   <img width="1920" height="1080" alt="Screenshot 2025-11-11 115152" src="https://github.com/user-attachments/assets/94ac49f1-8008-40f6-89aa-0fad51bb2853" />


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
<img width="1031" height="465" alt="Screenshot 2025-11-11 120334" src="https://github.com/user-attachments/assets/c004028f-5e0c-4b5c-a7a2-90e3f3ee27fb" />


CASE 2: LED OFF
<img width="1032" height="468" alt="Screenshot 2025-11-11 120352" src="https://github.com/user-attachments/assets/d87e6984-ee49-4f9d-b300-fdb930d9bfbe" />


---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




