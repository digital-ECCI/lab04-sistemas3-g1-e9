[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/0V8i2zWk)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23550238&assignment_repo_type=AssignmentRepo)
# Lab04: Visualización de Datos en Raspberry Pi con Node-RED 

## Integrantes

sebastian organista 
edwar carrero 
yesid alfonso

## Documentación


1. Introducción
Node-RED es una herramienta de programación visual basada en flujos, diseñada para conectar dispositivos, APIs y servicios en línea de manera sencilla. Permite crear aplicaciones mediante una interfaz gráfica donde se arrastran y conectan nodos que representan funciones o servicios.

Node-RED se ejecuta sobre Node.js, una plataforma que permite ejecutar código JavaScript del lado del servidor de forma eficiente y escalable. Además, utiliza npm (Node Package Manager), el gestor de paquetes que facilita la instalación de módulos y librerías.
2. Requisitos
Software:
- Raspberry Pi OS
- Acceso SSH
- Node.js y npm
- Node-RED
- Python 3

Conectividad:
- Red local compartida
- Acceso por SSH
- Navegador web
3. Procedimiento
3.1 Conexión por SSH:
ssh usuario@ip

3.2 Instalación de Node-RED:
bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)

3.3 Ejecución local:
node-red-pi --max-old-space-size=256
Acceso: http://ip:1880

3.4 Ejecución automática:
sudo systemctl enable nodered.service
sudo reboot
4. Interfaz de Node-RED
- Workspace: área de trabajo
- Palette: nodos disponibles
- Nodes: bloques funcionales
- Connections: flujo de datos
- Deploy: ejecutar cambios
- Debug: monitoreo
- Dashboard: interfaz gráfica
5. Creación de flujo
Nodos utilizados:
- Color picker
- Text input
- Function
- Debug
- Write file


6. Diagrama de flujo



7. Resultados
- Instalación exitosa
- Flujo funcional creado
- Ejecución automática configurada


<!-- Incluir diagramas y adjuntar al repositorio, en una carpeta src, el flujo que crearon -->


## Conclusiones
