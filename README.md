# ESJV-Model1-Photogrammetry-Scanner
Repositorio con todos los códigos y archivos necesarios para el funcionamiento de un escáner de fotogrametría con captura y envío automático de fotos a Google Drive

Para el desarrollo de este proyecto se utilizó un Arduino UNO y una ESP32 Wrover Module conectadas a través de un sistema de relé + transistor el cual se activa al comenzar el programa de fotogrametría.
Además de ese modo, el programa cuenta con 2 modos adicionales (cinemático y control manual) para diagnósticos adicionales o mantenimiento en caso de ser necesario

Materiales:
 - Arduino UNO
 - ESP32 Wrover Cam
 - Motor paso a paso + Driver
 - Adaptador de voltaje 12V a 5V
 - Módulo Relé 24V 10A
 - Display LCD
 - Módulo Joystick
 - Potenciómetro 20 kΩ
 - 1 Resistencia 330 Ω
 - PCB impreso

Para su correcto funcionamiento, se debe crear un archivo Google Script en el Google Drive que recibirá las imágenes con el contenido del archivo "Google Script.txt". Una vez listo, se debe **Implementar** el archivo como **Aplicación Web** y se obtendrá el **ID de implementación** el cual hay que incluir en el código de la ESP32 Wrover Cam.

const folderName = e.parameters.folder || 'ESP32-CAM' (Google Script)  --->    String myMainFolderName = "ESP32-CAM";   (Código ESP32 Wrover Cam)

Esta línea se llenará con el nombre de la carpeta de Google Drive en donde se almacenarán los archivos. Puede crearla previamente, o si no el Google Script se encargará de crearla automáticamente.
String myDeploymentID = "xxxxxx"

El código de la ESP32 Wrover Cam debe estar acompañado de los archivos Base64.h y Base64.c. Además se debe de seleccionar el esquema de partición como "Huge App" para poder subir el código.
Se recomienda usar un adaptador de corriente AC con salida de 12V 1~2A por el alto consumo de corriente del motor y la cámara OV2640.
