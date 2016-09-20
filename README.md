# video-y-telemetria-con-ser2net
Video 1080 y telemetria por wifi con ser2net y gstreamer
INSTALACION.

1.Descargamos la imagen iso.
ALTERNATIVA

2.Formateamos la tarjeta con SD formater
  a. Escribimos con Win32DiskImager la imagen en la sd.

3.Seguidamente con putty habrimos la consola de raspberry .

4.Descargamos el siguiente archivo para raspberry pi 3 
 Descargamos este para raspberry pi 2

Y lo pegamos en la consola de putty

5.Le damos a intro y esperamos a que realice la instalación, después: sudo reboot

6.Solo conectamos tx y rx , alimentamos raspberry pi con un bec independiente.

IMAGEN DE CONECCION

http://ardupilot.org/dev/_images/RaspberryPi_Pixhawk_wiring1.jpg

6.Se necesita para conexión por wifi un  usb dual banda compatible con raspberry, yo utilizo csl 300.

7.Tambien se requiere un punto de acceso o ruter de 5G, yo utilizo ubikiti M5

6. Raspberry conecta automáticamente a ssid:ruter y comtraseña:2004123413252.

7. Para cambiar ssid o comtraseña entrar en cd /etc/wpa_supplicant
Sudo nano wpa_supplicant.conf

8. Raspberry pi envía telemetría por tcp .
 Video por UDP con gstreamer en wifi 5G.

9. Para cambiar opciones de video entrar en. /home/pi/video
Desactivar video: sudo systemctl disable video
Activar video: sudo systemctl enable video
Parar video: sudo systemctl stop video
Comenzar video: sudo systemctl start video
 
10.Para cambiar opciones video mobil entrar en /home/pi/video-mobil.
Desactivar video: sudo systemctl disable video-mobil
Activar video: sudo systemctl enable video-mobil
Parar video: sudo systemctl stop video-mobil
Comenzar video: sudo systemctl start video-mobil

11.Para conectar a mision Planner utilizar 
TCP:57600  
IP:192.168.1.122  
Puerto:2001.

12.Para que se realice coneccion, el punto de acceso tiene que tener habilitado  ip fija.
 Descargar archivo de configuración de ubiquiti M5

13.En pc tiene que tener la ip fija 192.168.1.150

14.En mobil tiene que tener la ip fija 192.168.1.80.

15.Para los que tengáis problemas por alimentar pincho wifi desde raspi por el usb se puede quitar restriccion de consumo modificando el siguiente archivo:

sudo nano /boot/config.txt

Dentro de este archivo ponemos lo siguiente al final del archivo.

max_usb_current=1

safe_mode_gpio=4

después comtrol+o
y comtrol +x.
16. Aquí tenéis plugin para ver video en misión Planer

17.Instalais mision planner y despues el plugin.

18.Teneis que descargar Gstreamer e instalar en el pc.

20.Aqui teneis un scripts para ver el video en pc con gstremer:https://github.com/5jjCopter/video-y-telemetria-con-ser2net/blob/master/video-pc.bat , ejecutar como administrador cuando estemos trasmitiendo video con raspberrry

21.Este es el pipeline que yo utilizo en gstreamer que hay que seleccionar en el menu de configuracion.

udpsrc port=9000  buffer-size=60000 ! application/x-rtp,encoding-name=H264,payload=96 ! rtph264depay ! h264parse ! queue ! avdec_h264

Actualizacion

Archivo configuracion ubiquiti M5: https://drive.google.com/file/d/0B3LYYl80mki7UmNXU0RpMkRzOW8/view?usp=sharing

Archivo configuracion Ubiquiti Lite Beam M5: https://drive.google.com/file/d/0B3LYYl80mki7SjhXN01lZzh1Nk0/view?usp=sharing

Archivo actualizacion firmware Ubiquiti Lite Beam M5: https://drive.google.com/file/d/0B3LYYl80mki7ZHplQ1BOTjRHVFU/view?usp=sharing



