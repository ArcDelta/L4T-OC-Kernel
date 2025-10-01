# Switch L4T-OC-Kernel 
**DISCLAIMER: USE AT YOUR OWN RISK!**

This Kernel is dangerous and can possibly damage your console. Therefore I do not recommend using this project. If you decide to use it, USE AT YOUR OWN RISK. THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND.

Overclocking in general will shorten the lifespan of some hardware components.<br>
**YOU ARE RESPONSIBLE for any problem or potential damage**


## Features
- Custom CPU SLT Table (2601-2703 MHz)
- Custom GPU SLT/HiOPT Table (1267-1305 MHz)
- 64 CPU LUT Table (Erista & Mariko Supported)
- CPU UV Override 1-6 
- CPU High Freq vMin Override
- Increased SoC / CPU / GPU vMin
- 1250 mV VDD2
- 40/45/48/50Hz Refresh Rate Support
- LiHV Battery Upgrade Support 
- Nyxi Joycon Support
- Reworked NVPModel profiles


## How to use 
1. Download latest [release](https://github.com/NaGaa95/L4T-OC-Kernel/releases)
 
2. Replace in Switchroot/Ubuntu folder :<br>
`uImage` / `nx-plat.dtimg` / `modules.tar.gz` / `boot.scr`

### **L4T.ini Configuration :**

 `dvfsb=1`

 `gpu_dvfsc=1`

 `cpu_uv=` (1-6 - Recommended 4)

 `cpu_hmin=` (Desired value in mV - Default 850)
<br><br>

⚠️ **ONLY FOR BATTERY UPGRADE - MAKE SURE YOUR BATTERY IS ABLE TO HANDLE 4.32V** ⚠️ <br>
`lihv=1` (Set max charging voltage to 4.32v)
<br><br>
### **Optional :** <br>
Replace `nvpmodel_t210b01.conf` in `/etc/nvpmodel/nvpmodel_t210b01.conf` **(NEED ROOT ACCESS)**

0. Low Power   : 1785 - 614
1. Handheld    : 1963 - 921
2. OC CPU      : 2703 - 921
3. OC GPU      : 1963 - 1305
4. Performance : 2193 - 1075
5. L4T SLT     : 2397 - 1228
6. PMIC Burner : 2703 - 1305

## Info

**Do not use higher than 2397 MHz without setting CPU UV in your L4T.ini file ⚠️** <br>
Without UV, it will use high voltage, and the actual frequency will be much lower than what Tegrastats reports

Be careful when using a high CPU UV preset with a low **`cpu_hmin`** value, as it can cause instability at **1963-2193 MHz**

On **Switch Lite**, CPU is now limited to **2397 MHz** and GPU to **1228 MHz**
It may shut down when running on battery if the power draw is too high ⚠️ <br>
It's recommended to use it with a charger connected or limit frequency via NVPModel profiles

### **Commands :** <br>
CPU Rate :<br>
`watch -n1 sudo cat /sys/kernel/debug/tegra_dfll_fcpu/rate`

CPU Voltage :<br>
`sudo cat /sys/kernel/debug/tegra_dfll_fcpu/output_mv`

GPU Voltage :<br>
`sudo cat /sys/kernel/debug/57000000.gpu/voltage`

RAM VDDQ :<br>
`sudo cat /sys/kernel/debug/regulator/vdd-ddr/regulator/microvolts`

RAM VDD2 :<br>
`sudo cat /sys/kernel/debug/regulator/vddio-ddr/regulator/microvolts`

## Sources : 
[l4t-kernel-build-scripts](https://github.com/NaGaa95/l4t-kernel-build-scripts)<br>
[switch-l4t-kernel-4.9](https://github.com/NaGaa95/switch-l4t-kernel-4.9)<br>
[switch-l4t-kernel-nvidia](https://github.com/NaGaa95/switch-l4t-kernel-nvidia)<br>
[switch-l4t-kernel-nvgpu](https://github.com/NaGaa95/switch-l4t-kernel-nvgpu)<br>
[switch-l4t-platform-t210-nx](https://github.com/NaGaa95/switch-l4t-platform-t210-nx)

## Acknowledgement
[CTCaer](https://github.com/CTCaer/) <br>
[Azkali](https://github.com/Azkali) <br>
[Meha](https://github.com/hanai3Bi) <br>
[b3711](https://github.com/halop/)
