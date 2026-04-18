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

<img width="1024" height="1536" alt="node-red diagrama" src="https://github.com/user-attachments/assets/be6206be-4d8f-4162-b805-4dc8b123bd63" />


7. Resultados
- Instalación exitosa
- Flujo funcional creado
- Ejecución automática configurada

        function colorNameToHex(name) {
            const colores = {
                'rojo': '#ff0000',
                'verde': '#00ff00',
                'azul': '#0000ff',
                'amarillo': '#ffff00',
                'cyan': '#00ffff',
                'magenta': '#ff00ff',
                'blanco': '#ffffff',
                'negro': '#000000',
                'gris': '#808080',
                'naranja': '#ffa500',
                'morado': '#800080',
                'rosa': '#ffc0cb',
                'marron': '#a52a2a',
                'celeste': '#87ceeb',
                'violeta': '#ee82ee',
                'turquesa': '#40e0d0',
                'dorado': '#ffd700',
                'plateado': '#c0c0c0'
            };
            return colores[name.toLowerCase()] || null;
        }
        
        // Función para convertir color string a HEX
        function rgbStringToHex(rgbString) {
            var match = rgbString.match(/rgb\((\d+),\s*(\d+),\s*(\d+)\)/);
            if (match) {
                var r = parseInt(match[1]);
                var g = parseInt(match[2]);
                var b = parseInt(match[3]);
                return '#' + ((1 << 24) + (r << 16) + (g << 8) + b).toString(16).slice(1);
            }
            return null;
        }
        
        // Función para convertir HEX a color
        function hexToRgb(hex) {
            hex = hex.replace('#', '');
            var r = parseInt(hex.substring(0, 2), 16);
            var g = parseInt(hex.substring(2, 4), 16);
            var b = parseInt(hex.substring(4, 6), 16);
            return { r: r, g: g, b: b };
        }
        
        // Obtener el valor de entrada
        var inputValue = msg.payload;
        var colorHex = null;
        var fuente = 'desconocida';
        
        if (typeof inputValue === 'string') {
            if (inputValue.startsWith('#')) {
                colorHex = inputValue;
                fuente = 'hexadecimal';
            }
            else {
                var nombreColor = colorNameToHex(inputValue);
                if (nombreColor) {
                    colorHex = nombreColor;
                    fuente = 'nombre_color';
                }
                else if (inputValue.includes('rgb(')) {
                    var rgbHex = rgbStringToHex(inputValue);
                    if (rgbHex) {
                        colorHex = rgbHex;
                        fuente = 'rgb_string';
                    }
                }
            }
        }
        else if (typeof inputValue === 'object' && inputValue.hex) {
            colorHex = inputValue.hex;
            fuente = 'selector_color';
        }
        else if (typeof inputValue === 'string' && inputValue.length === 7 && inputValue.startsWith('#')) {
            colorHex = inputValue;
            fuente = 'selector_color';
        }
        
        if (colorHex && colorHex.startsWith('#')) {
            var rgb = hexToRgb(colorHex);
        
        // Crear mensaje de salida
        msg.payload = {
            hex: colorHex,
            red: rgb.r,
            green: rgb.g,
            blue: rgb.b,
            rgb_string: `rgb(${rgb.r}, ${rgb.g}, ${rgb.b})`,
            fuente: fuente,
            entrada_original: inputValue,
            timestamp: new Date().toISOString()
        };
        
        // Mostrar en consola para debugging
        node.warn(`Color procesado: ${colorHex} (${fuente})`);
        
        return msg;
        } else {
        // Si no se pudo procesar, mostrar error
        node.warn(`No se pudo procesar: "${inputValue}"`);
        return null;}
    <!-- Incluir diagramas y adjuntar al repositorio, en una carpeta src, el flujo que crearon -->


## Conclusiones
