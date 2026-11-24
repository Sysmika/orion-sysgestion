# Cambios

## 0.1.4

- El panel aparece también para los usuarios de Home Assistant que no son administradores (el personal del comercio u oficina). En Nexus lo ven los clientes de Comercio y Oficina; en el equipo demo, solo los usuarios de esos rubros.

## 0.1.3

- Nueva página **Diagnóstico** (botón "Ver diagnóstico" en cada aviso de error): prueba paso a paso la configuración, la conexión con el sistema de gestión, la entrada `/sso/nexus.php` y la validación con Orion AR, y marca con ❌ el primer paso que falla, con el código y el detalle del servidor.
- El aviso `orion_ar_no_disponible` ahora dice claramente que es el sistema de gestión el que no logra hablar con Orion AR, no Home Assistant.
- `/salud` devuelve JSON con el resultado del último intento, y Home Assistant lo usa como watchdog para reiniciar el add-on si se cuelga.
- El registro muestra el motivo real de los errores de conexión (DNS, certificado, tiempo agotado) y avisa si `/sso/nexus.php` no responde JSON.

## 0.1.2

- Si el sistema de gestión manda un campo `detalle` al rechazar el acceso, el Registro del add-on lo muestra (sirve para diagnosticar sin entrar al servidor).

## 0.1.1

- Los avisos de error salen con código 200, para que Cloudflare u otro proxy no los reemplace por su página genérica ("502 Bad Gateway") y se vea el motivo real.

## 0.1.0

- Primera versión. Abre el sistema de gestión Orion del cliente desde el menú lateral de Home Assistant, sin pedir usuario ni clave.
- El sistema sigue en la web, independiente: el add-on pide un token de un solo uso a `/sso/nexus.php` con la API key de la instalación, y el sistema la valida contra Orion AR.
- Dos formas de abrirlo: dentro de Home Assistant (marco) o en una ventana nueva.
- Solo atiende pedidos que llegan por Ingress de Home Assistant. No guarda datos del sistema.
