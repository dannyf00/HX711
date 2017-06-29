# HX711

I have received quite a few inquries about the HX711 work that I have done. The original user space code is gone so I thought I would post the HX711 driver itself.

The user needs to specify two pins to / from HX711: 

```
//hardware configuration
#define HX711DIN_PORT			PINB		//an input port from HX711 to the mcu
#define HX711DIN_DDR			DDRB
#define HX711DIN				  (1<<2)

#define HX711SCK_PORT			PORTB   //output port from the mcu to HX711
#define HX711SCK_DDR			DDRB
#define HX711SCK				  (1<<3)
//end hardware configuration
```


The routines fall into three categories:

1) initialization, done by calling hx711_init();

2) reading HX711 status: hx711_busy();

3) reading from hx711, Channel A (128x and 64x gain) and Channel B (64x gain), done by calling hx711_readA128()/hx711_readA64() and hx711_readB64(), respectively.

