# video-y-telemetria-con-ser2net
Video 1080 y telemetria por wifi con ser2net
Instalacion.

1.Descargamos la imagen iso desde:https://drive.google.com/file/d/0B3LYYl80mki7WXlOM2dyQzlPMVE/view?usp=sharing

ALTERNATIVA:https://www.dropbox.com/s/iwme9fs5ie32fh9/mavproxy-5jjcopter.7z?dl=0

2.Escrivimos con Win32DiskImager la imagen en la sd.

3.Seguidamente con putty habrimos la consola .

4.descargamos el siguiente archivo:https://github.com/5jjCopter/video-y-telemetria-con-ser2net/blob/master/install

5.Le damos a intro y esperamos a que realize la instalacion, despoues sudo reboot.

6.Solo conectamos tx y rx y alimentamos raspberry pi con un bec independiente.

IMAGEN DE CONECCION

http://ardupilot.org/dev/_images/RaspberryPi_Pixhawk_wiring1.jpg

6.Se nesesita para coneccion por wifi usb dual banda compatible con raspberry, yo utilizo csl 300.

7.Tambien se requiere un punto de acceso o ruter de 5G, yo utilizo ubikiti M5

6. Raspberry conecta automaticamente a ssid:ruter y comtraseña:2004123413252.

7. Para cambiar ssid o comtraseña entrar en /etc/network/interfaces
8. 
8. Raspberry pi envia telemetria por tcp y video por gstermer por wifi 5G.
9. 
9. Para cambiar opciones de video entrar en. /home/pi/video
10. 
10.Para cambiar opciones video mobil entrar en /home/pi/video-mobil.

11.Para conectar a mision Planner utilizar TCP:57600 IP:192.168.1.122 Puerto:2001.

12.Para que se realice coneccion el punto de acceso tiene que tener habilitado la ip fija.

13.En pc tiene que tener la ip fija 192.168.1.150

14.En mobil tiene que tener la ip fija 192.168.1.80.

15.Para los que tengais ploblemas por alimentar pincho wifi desde raspi por el usb se puede quitar restriccion de consumo modificando el siguiente archivo:

sudo nano /boot/config.txt

Dentro de este archivo ponemos lo siguiente al final del archivo.

max_usb_current=1

safe_mode_gpio=4

despues comtrol+o
y comtrol +x.



