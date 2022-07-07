# arduino uno (or any atmega328p for this example) and adxl345 - Klipper0.10.0
 

## Steps
1. Get arduino uno (or any atmega328p for this example) and adxl345
2. run make menu config and setup for your crystal speed (usually 16mhz) and atmega 328p
3. make 
4. avrdude -carduino -patmega328p -P/dev/ttyUSB0 -b115200 -D -Uflash:w:out/klipper.elf.hex:i
4. get mcu port from KIAUH example : "/dev/serial/usb-1a86_USB2.0-Ser_-if00-port0" and add new MCU with new port to print config 
5. add info about new accelerometer to config
4. test in console with ACCELEROMETER_QUERY

# pin choice
## Arduino aliases for atmega168/328/328p boards
[for other board pinouts click here](https://github.com/Klipper3d/klipper/blob/master/config/sample-aliases.cfg)
[board_pins arduino-standard]
aliases:
    ar0=PD0, ar1=PD1, ar2=PD2, ar3=PD3, ar4=PD4,
    ar5=PD5, ar6=PD6, ar7=PD7, ar8=PB0, ar9=PB1,
    ar10=PB2, ar11=PB3, ar12=PB4, ar13=PB5, ar14=PC0,
    ar15=PC1, ar16=PC2, ar17=PC3, ar18=PC4, ar19=PC5,
    analog0=PC0, analog1=PC1, analog2=PC2, analog3=PC3, analog4=PC4,
    analog5=PC5, analog6=PE2, analog7=PE3
	
## pin out	
![Arduino uno SPI pinout](https://www.etechnophiles.com/wp-content/uploads/2020/11/SPI.png)

## print.cfg pins
[adxl345]
cs_pin: arduino:PB2
spi_software_sclk_pin: arduino:PB5
spi_software_mosi_pin: arduino:PB3
spi_software_miso_pin: arduino:PB4

## TroubleShooting
[If your Arduino klipper firmware wont compile check here](https://github.com/Klipper3d/klipper/issues/4938#issuecomment-1094246978)
	try -b250000 (or a slower baud rate) if you are out of sync and get stk500 errors when using avrdude.