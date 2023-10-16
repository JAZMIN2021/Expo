Vargas Vargas Jazmin Angelica 20212436
# Hola Mundo

![HolaMundo](https://github.com/JAZMIN2021/Expo/assets/79472215/94d26af4-2c7a-4a0e-b33a-117fa2cad264)
  
  -- Utiles
- [x] Raspberry Pi
- [x]  Protoboard
- [x] Oled 1306
- [x] Cable Micro US
  
- [Codigo en Wokki](#recursos-adicionales)
![image](https://github.com/JAZMIN2021/Expo/assets/79472215/4fa450ed-99da-4bf9-8fd7-440ef96a0052)

- [Ejemplo de Código en Thonny](#ejemplo-de-c%C3%B3digo)
 
  Utilizando Python 
```python
import utime
from ssd1306 import SSD1306_I2C
import ssd1306
from machine import Pin, I2C  # for LED

# Configura los pines SDA y SCL para la comunicación I2C
i2c = machine.I2C(0, sda=machine.Pin(8), scl=machine.Pin(9))
#Configura el objeto SSD1306 para la pantalla OLED
oled = ssd1306.SSD1306_I2C(128, 64, i2c)
led = Pin("LED", Pin.OUT)
led.on()

# Limpia la pantalla
oled.fill(0)
oled.show()

# Presentacion en pantalla en la pantalla
oled.text("20212436 VVJA", 0, 0)
oled.text("Hola Mundo", 0, 16)
oled.show()
