# STM32H7A3-W25Q128-External-Loader
## W25Q128 External Loader for STM32H7A3VIT6

This is a modified fork compatible with the STM32H7A3VIT6 chip variant. The difference between this repository and the original branch is that there are changes to MPU configuration settings to allow the loader to access memory regions at 0x90000000 - 0x9FFFFFFF after the chip is memory mapped. 

## Pin Out:

![Pinout-2](https://raw.githubusercontent.com/jmcrafty/STM32H7A3-W25Q128-External-Loader/main/.github/images/pinout.png)
This fork has an alternate pinout that can easily be changed in the STM32CubeIDE Configuration GUI.

## OCTOSPI Configuration:
### 
### 
![0](https://raw.githubusercontent.com/jmcrafty/STM32H7A3-W25Q128-External-Loader/main/.github/images/config.png)

The system clock for the STM32H7A3VIT6 is 280 MHz and the W25Q128 is configured for SDR mode (opposed to DTR)
|Clock Prescalar | The maximum frequency of OCTOSPI from the datasheet for SDR mode is 80 MHz, so the clock prescalar is set to 4 because 280 / 4 = 70 MHz < 80 MHz |
|Chip Select High Time | Per the W25Q128 datasheet the longest non-read CS deselect time (tCSH) is 50 ns. 50 ns / 4 prescaler * 280 MHz / 1000 = 3.5 cycles, round up to 4 |
|Sample Shifting | Sample shifting (SSHT) should be enabled in SDR mode and disabled in DTR mode |
|Delay Hold Quarter Cycle | Delay hold quarter cycle (DHQC) should be enabled in DTR mode and disabled in SDR mode |

## MPU Configuration:
### 
### 
![0](https://raw.githubusercontent.com/jmcrafty/STM32H7A3-W25Q128-External-Loader/main/.github/images/mpu.png)

## Project Properties
### cmd.exe /C copy/Y "${BuildArtifactFileBaseName}.elf" "..\W25Q128_STM32H7A3VIT6.stldr"
###
![3](https://raw.githubusercontent.com/jmcrafty/STM32H7A3-W25Q128-External-Loader/main/.github/images/settings1.png)
###
### 
### 
### Change Linker Script file. Click Browse and choose "linker.ld"
### Uncheck "Discard Unused Sections (-WL,--gc-sections)"
###
![4](https://raw.githubusercontent.com/jmcrafty/STM32H7A3-W25Q128-External-Loader/main/.github/images/settings2.png)
