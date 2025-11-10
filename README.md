# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
<img width="692" height="432" alt="Screenshot 2025-11-04 223247" src="https://github.com/user-attachments/assets/06296fb0-84c3-4c3b-903f-14728a51b528" />

2. Click **File → New STM32 Project**.
<img width="692" height="432" alt="image" src="https://github.com/user-attachments/assets/36de05fa-be2f-4ddb-8a31-b8277142e2e0" />

3. Select the **target microcontroller** or board and click **Next**.
<img width="692" height="432" alt="image" src="https://github.com/user-attachments/assets/b00c5512-da93-4074-b61f-57ce66ef77c9" />



4. Name the project.
<img width="692" height="432" alt="image" src="https://github.com/user-attachments/assets/0db3d533-db37-47ba-b28b-c72eea4d3e42" />

5. The corresponding `.ioc` file will be generated automatically.
<img width="692" height="432" alt="image" src="https://github.com/user-attachments/assets/674457b0-86a8-42b6-b74d-2b867d747adf" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
<img width="692" height="432" alt="image" src="https://github.com/user-attachments/assets/46228acd-8a0e-4728-b9fc-44fe7b0e42e8" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
<img width="692" height="432" alt="image" src="https://github.com/user-attachments/assets/c7858cd4-b53d-4e98-a22d-bde9bd5d74ff" />
 
8. Edit the generated main program as required.
<img width="692" height="432" alt="image" src="https://github.com/user-attachments/assets/237df7d6-55bc-46b7-b460-1b87341a0300" />

9. Click **Project → Build All**.
<img width="692" height="432" alt="image" src="https://github.com/user-attachments/assets/e16d4f12-d802-4327-8112-504ed0da54f1" />

10. Link the **HEX file** using the post-build process.
<img width="691" height="143" alt="image" src="https://github.com/user-attachments/assets/4e68fa56-0e98-46c5-9d7d-772f3829032a" />

11. Click **Debug** and connect the **STM Nucleo Board**.
<img width="692" height="432" alt="image" src="https://github.com/user-attachments/assets/a17f388d-a405-469d-9e7d-851d794f5993" />
    
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
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

<img width="551" height="345" alt="Screenshot 2025-10-29 020842" src="https://github.com/user-attachments/assets/200674ef-1aca-41b3-9ed6-3f723bc5e444" />

CASE 2: LED OFF

<img width="551" height="345" alt="Screenshot 2025-10-29 020842" src="https://github.com/user-attachments/assets/102cd817-fb82-4e2d-a099-07299ffd68ea" />

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
