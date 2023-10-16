Vargas Vargas Jazmin Angelica 20212436

### Hora WIFI

![Hora de Internet](https://github.com/JAZMIN2021/Expo/assets/79472215/6d8ea2b8-1e49-47e0-bfcc-c3e308f55cde)
  
  -- Utiles
- [x] Raspberry Pi
- [x]  Protoboard
- [x] Oled 1306
- [x] Cable Micro US
  
- [Codigo en Wokki](#recursos-adicionales)
![image](https://github.com/JAZMIN2021/Expo/assets/79472215/d55cda7d-9a2b-4496-8166-ef6df42dd6b0)

- [Ejemplo de Código en Thonny](#ejemplo-de-c%C3%B3digo)
 
  Utilizando Python 
```python
#Importacion de las librerias
from machine import Pin, I2C
from ssd1306 import SSD1306_I2C
import utime
import ntptime

# Configuración de la pantalla OLED y pines I2C
pix_res_x = 128
pix_res_y = 64
scl_pin = 27
sda_pin = 26

def init_i2c(scl_pin, sda_pin):
    # Inicializa el dispositivo I2C
    i2c_dev = I2C(1, scl=Pin(scl_pin), sda=Pin(sda_pin), freq=400000)
    return i2c_dev

def update_time():
    try:
        # Sincroniza la hora con un servidor NTP (usando el servidor predeterminado)
        ntptime.host = 'time.google.com'
        print("Hora actual actualizada desde Internet:", utime.localtime())
    except OSError as e:
        print("Error al sincronizar la hora desde Internet:", e)

def display_time(oled, time_data):
    oled.fill(0)  # Limpia la pantalla
    oled.text("Tijuana B.C, Mexico", 40, 32)
    oled.text("Mexico", 62, 47)
    oled.text("Hora actual:", 0, 0)
    oled.text("{:02d}:{:02d}:{:02d}".format(time_data[3], time_data[4], time_data[5]), 0, 16)
    oled.show()

def main():
    i2c_dev = init_i2c(scl_pin, sda_pin)
    oled = SSD1306_I2C(pix_res_x, pix_res_y, i2c_dev)
    
    while True:
        update_time()  # Actualiza la hora desde Internet
        current_time = utime.localtime()
        
        # Muestra la hora en la pantalla OLED
        display_time(oled, current_time)
        utime.sleep(1)

if __name__ == '__main__':
    main()




