# Informe de Auditoría de Red Wi-Fi Insegura

Actividad: Seguridad en redes Wi-Fi públicas  
Herramienta de análisis:Firefox Developer Tools – Network  
Sitio analizado:http://neverssl.com  
Sistema operativo: Windows 10 de 64 bits

---

# 1. Introducción

El objetivo de esta práctica es analizar el tráfico generado al ingresar a un sitio web que utiliza el protocolo HTTP y comprender los riesgos que esto representa, especialmente cuando nos conectamos a redes Wi-Fi públicas.

Para realizar el análisis se utilizó la herramienta de desarrollador del navegador Firefox, específicamente la pestaña Network (Red), que permite observar las solicitudes realizadas entre el navegador y el servidor.

A partir de los datos obtenidos, se analizaron los encabezados HTTP, el protocolo utilizado y los posibles riesgos relacionados con la privacidad y la seguridad de la información.

## 2. Sitio analizado

Para realizar la práctica se ingresó al siguiente sitio:

- URL:http://www.neverssl.com/online/
- Host: www.neverssl.com
- Método HTTP: GET
- Protocolo: HTTP/1.1
- Código de respuesta: 200 OK

El sitio utiliza HTTP, un protocolo que no cifra por sí mismo la comunicación entre el navegador y el servidor. Por este motivo, el navegador indica que la conexión no es segura.

## 3. Evidencia observada

Durante el análisis de tráfico se identificaron diferentes datos correspondientes a la solicitud realizada.

### 3.1. Datos generales de la solicitud

Los principales datos observados fueron:

| Parámetro | Resultado |
|---|---|
| Método | GET |
| Host | www.neverssl.com |
| Ruta | /online/ |
| Protocolo | HTTP/1.1 |
| Estado | 200 OK |
| Tipo de contenido | text/html; charset=UTF-8 |

El código 200 OK indica que el servidor recibió y procesó correctamente la solicitud.

### 3.2. Encabezados HTTP (Request Headers)

También se identificaron diferentes encabezados enviados por el navegador:

- Host:www.neverssl.com
- Accept: indica los tipos de contenido que acepta el navegador.
- Accept-Encoding:gzip, deflate.
- Accept-Language:en-US,en;q=0.9.
- Connection:keep-alive.
- Referer: https://www.bing.com/
- User-Agent:Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:160.0) Gecko/20100101 Firefox/160.0.

El encabezado User-Agent permite identificar información sobre el navegador y el sistema operativo utilizado para realizar la solicitud.

Evidencia 1: Solicitud HTTP

![Solicitud HTTP](./01_solicitud_http.png)

*Figura 1. Solicitud realizada al sitio NeverSSL, donde se observa el método GET, el protocolo HTTP/1.1 y el Host.*

Evidencia 2: Encabezados de la solicitud*

[solicitud Headers](./02_solucitud_headers.png)

*Figura 2. Encabezados HTTP enviados por el navegador, incluyendo Host, Referer y User-Agent.*

## 4. Riesgos encontrados

Utilizar HTTP en una red Wi-Fi pública puede representar un riesgo para la privacidad y seguridad de los usuarios.

Al no existir cifrado TLS en la comunicación HTTP observada, un atacante con capacidad de interceptar el tráfico de la red podría acceder a información transmitida entre el dispositivo y el servidor.

Entre los principales riesgos se encuentran:

1. Intercepción de datos (Sniffing): un atacante podría capturar paquetes de información que circulan por la red y analizar su contenido.
2. Ataques Man-in-the-Middle: un atacante podría intentar ubicarse entre el usuario y el servidor para interceptar o modificar las comunicaciones.
3. Exposición de información: determinados datos de las solicitudes, como las direcciones visitadas y los encabezados HTTP, pueden quedar visibles para quienes logren observar el tráfico.
4. Redes falsas (Evil Twins): un atacante puede crear una red Wi-Fi con un nombre similar al de un establecimiento legítimo para engañar a los usuarios y controlar su conexión.

Estos riesgos demuestran por qué es importante tener precaución al conectarse a redes inalámbricas públicas.

## 5. ¿Cómo ayuda una VPN?

Una VPN (Virtual Private Network) permite establecer una conexión cifrada entre el dispositivo del usuario y un servidor VPN mediante un túnel seguro.

Este mecanismo utiliza cifrado y encapsulamiento para proteger el tráfico que circula por la red pública.

Aunque un atacante pueda capturar los paquetes que se transmiten por la Wi-Fi, no podrá leer fácilmente su contenido porque los datos viajan cifrados dentro del túnel VPN.

Entre sus principales beneficios se encuentran:

- Cifrado: protege la información transmitida frente a observadores de la red local.
- Encapsulamiento:los paquetes originales se transportan dentro de otros paquetes protegidos.
- Túnel seguro:establece una comunicación protegida entre el dispositivo y el servidor VPN.
- Privacidad: dificulta que terceros en la red pública puedan observar directamente el tráfico original.

Es importante aclarar que una VPN no reemplaza al protocolo HTTPS. La VPN protege el tráfico hasta el servidor VPN, mientras que HTTPS protege la comunicación entre el navegador y el sitio web.

## 6. Las 3 Reglas de Oro para utilizar redes Wi-Fi públicas

1. Utilizar una VPN.

Siempre que sea posible, conectarse mediante una VPN confiable para cifrar el tráfico y proteger la información frente a posibles atacantes de la red pública.

2. Verificar que los sitios utilicen HTTPS.

Antes de ingresar contraseñas o información personal, comprobar que la dirección del sitio comience con HTTPS y que el certificado sea válido. Evitar ingresar datos sensibles en páginas que utilicen HTTP.

3. Evitar operaciones sensibles en redes públicas.

No realizar operaciones bancarias ni ingresar información confidencial cuando se utiliza una red Wi-Fi desconocida. También es recomendable desactivar la conexión automática a redes públicas y el uso compartido de archivos.

## 7. Conclusión

A través de esta práctica pude observar cómo se realiza una solicitud HTTP y qué información puede obtenerse mediante las herramientas de análisis de tráfico del navegador.

El análisis permitió identificar el Host, el método GET, el protocolo HTTP/1.1 y diferentes encabezados enviados por el navegador.

También pude comprender los riesgos que implica navegar sin cifrado en una red Wi-Fi pública y la importancia de utilizar herramientas como las VPN para proteger la información.

En conclusión, la seguridad al navegar no depende solamente de las herramientas utilizadas, sino también de los hábitos de cada usuario. Verificar los sitios web, utilizar conexiones cifradas y evitar compartir información sensible son medidas fundamentales para proteger nuestra privacidad.
