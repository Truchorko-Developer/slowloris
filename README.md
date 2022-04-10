# slowloris.py - Slowloris simple en Python

## ¿Qué es Slowloris?
Slowloris es básicamente un ataque de denegación de servicio HTTP que afecta a los servidores subprocesos. Funciona así:

1. Comenzamos a hacer muchas solicitudes HTTP.
2. Enviamos encabezados periódicamente (cada ~15 segundos) para mantener abiertas las conexiones.
3. Nunca cerramos la conexión a menos que el servidor lo haga. Si el servidor cierra una conexión, creamos una nueva y seguimos haciendo lo mismo.

Esto agota el grupo de subprocesos de los servidores y el servidor no puede responder a otras personas.

## Citación

Si encuentra útil este trabajo, por favor cítelo como

```bibtex
@article{luis498slowloris,
  title = "Slowloris",
  author = "Truchorko@luis498",
  journal = "github.com",
  year = "2015",
  url = "https://github.com/luis498/slowloris"
}
```

## ¿Cómo instalar y ejecutar?

Puede clonar el repositorio de git o instalarlo usando **pip**. Así es como lo ejecutas.

* `sudo pip3 install slowloris`
* `slowloris example.com`

Eso es todo lo que se necesita para instalar y ejecutar slowloris.py.

Si desea clonar usando git en lugar de pip, así es como lo hace.

* `git clone https://github.com/luis498/slowloris.git`
* `cd slowloris`
* `python3 slowloris.py example.com`

### Compatibilidad con proxy SOCKS5

Sin embargo, si planeas usar el `-x` opción para usar un proxy SOCKS5 para conectarse en lugar de una conexión directa a través de su dirección IP, deberá instalar el `PySocks` librería (o cualquier otra implementación de la `socks` biblioteca) también. [`PySocks`](https://github.com/Anorov/PySocks) es un tenedor de [`SocksiPy`](http://socksipy.sourceforge.net/) por el usuario de GitHub @Anorov y se puede instalar fácilmente agregando `PySocks` al `pip` comando anterior o ejecutarlo de nuevo así:

* `sudo pip3 install PySocks`

YA continuación, puede utilizar la opción `-x` para activar la compatibilidad con SOCKS5 y las opciones `--proxy-host` y `--proxy-port` para especificar el servidor proxy SOCKS5 y su puerto, si son diferentes del estándar ` 127.0.0.1:8080`.

## Opciones de configuración
Es posible modificar el comportamiento de slowloris con línea de comandos
argumentos Para obtener un documento de ayuda actualizado, simplemente ejecute
`slowloris -h`.

* -p, --port
* * Puerto del servidor web, generalmente 80
* -s, --sockets
* * Número de enchufes a utilizar en la prueba
* -v, --verbose
* * Aumenta el registro (salida en el terminal)
* -ua, --randuseragents
* * Aleatoriza a los agentes de usuario con cada solicitud
* -x, --useproxy
* * Use un proxy SOCKS5 para conectarse
* --https
* * Use HTTPS para las solicitudes
* --sleeptime
* * Tiempo para dormir entre cada encabezado enviado

## Licencia
El código está autorizado bajo la Licencia MIT.
