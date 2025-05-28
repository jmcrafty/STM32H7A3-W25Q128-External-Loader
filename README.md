# STM32H7A3-W25Q128-External-Loader
## W25Q128 External Loader for STM32H7A3VIT6

This is a modified fork compatible with the STM32H7A3VIT6 chip variant. The difference between this repository and the original branch is that there are changes to MPU configuration settings to allow the loader to access memory regions at 0x90000000 - 0x9FFFFFFF after the chip is memory mapped. This fork has an alternate pinout that can easily be changed in the STM32CubeIDE Configuration GUI.

## Pin Out:

![Pinout-2](https://raw.githubusercontent.com/jmcrafty/STM32H7A3-W25Q128-External-Loader/main/.github/images/pinout.png)

## OCTOSPI Configuration:
### 
### 
![0](https://raw.githubusercontent.com/jmcrafty/STM32H7A3-W25Q128-External-Loader/main/.github/images/config.png)

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
