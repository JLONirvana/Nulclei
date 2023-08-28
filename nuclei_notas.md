# Nuclei

Es una herramienta que permite ejecutar *pruebas de pentesting sobre aplicaciones web
y otros servicios*, lo que realmente le hace interesante es la capacidad de reducir
al máximo los falsos positivos.

Funciona con un modelos de plantillas en las que es necesario declaras cómo se deben
realizar las peticiones y qué debería hacer en la respuesta devuelta por el 
servidor para determinar que existe una vulnerabilidad, mala configuración
o fuga de información.

* para descargar nuclei la ruta de la url es
  - https://nuclei.projectdiscovery.io/nuclei/get-started/

para poder descargar a la ultima version se realiza lo siguiente
* descargar la ultima version desde github
    - https://github.com/projectdiscovery/nuclei/releases/tag/v2.9.10
```bash
wgt https://github.com/projectdiscovery/nuclei/releases/download/v2.9.10/nuclei_2.9.10_linux_amd64.zip
unzip nuclei_2.9.10_linux_amd64.zip
echo "el ejecutable mover a la carpeta"
sudo mv nuclei /usr/local/bin/
```
la ruta en Linux para encontrar las plantillas es:

```bash
cd /root/nuclei-templates
```
* para escanear una url sólo con los templates que tengan etiqueta del tipo CVE o SSL
```bash
nuclei -u https://intranet.pronabec.edu.pe/ -tags ssl
```
* para escanear una url sólo con un template en específico
```bash
nuclei -t <plantilla.yml> -u <url>
```
# clasificando los templates
* **SSL**

para verificar los certificados SSL la cual es **es un certificado digital que autentica la
identidad de un sitio web y habilita una conexion cifrada**. 
* La version del protocolos TLS que utiliza un sitio web 
    - /root/nuclei-templates/ssl/tls-version.yaml
* Para verificar los **cipher suites** debiles que se utliza dentro de los protocolos TLS
    - /root/nuclei-templates/ssl/weak-cipher-suites.yaml
* Para verificar los cifrados obsoletos que utiliza un sitio web
    - /root/nuclei-templates/ssl/deprecated-tls.yaml
    - se pueden encontrar mas informacion dentro de la carpeta SSL


* para verificar las cabeceras de seguridad faltantes de http.
    - /root/nuclei-templates/http/misconfiguration/http-missing-security-headers.yaml
