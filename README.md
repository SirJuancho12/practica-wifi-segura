# Informe de Auditoría de Red Wi-Fi Insegura

## Introducción

En esta práctica entré a un sitio que usa HTTP y miré con las herramientas del navegador qué datos se ven en la conexión. Después expliqué qué riesgos hay en una red Wi-Fi pública, cómo ayuda una VPN y armé mis 3 reglas para navegar más seguro.

## Sitio analizado

- **Sitio al que entré:** `http://neverssl.com`
- **Me redirigió a:** `http://wholefreshgrandmagic.neverssl.com/online/`
- **Host:** `wholefreshgrandmagic.neverssl.com`
- **Protocolo:** HTTP, o sea sin cifrar. El navegador lo marcó como "No seguro".

## Evidencia observada

Abrí las herramientas de desarrollador (F12), fui a la pestaña **Red**, recargué la página y miré la primera solicitud.

Lo que vi:

- **URL solicitada:** `http://wholefreshgrandmagic.neverssl.com/online`
- **Método:** `GET`
- **Estado:** `301 Moved Permanently` (me mandó a la misma página con una `/` al final)
- **Host:** `wholefreshgrandmagic.neverssl.com`
- **Dirección remota:** `34.223.124.45:80` (el puerto 80 es el de HTTP)
- **User-Agent:** `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/138.0.0.0 Safari/537.36`
- **Otros headers:** `Accept`, `Accept-Language`, `Accept-Encoding`, `Referer`, `Connection`, `Cache-Control`

<img width="556" height="1152" alt="capture" src="https://github.com/user-attachments/assets/3c8d88da-f16f-4da4-9c7e-feff26cf1ede" />

Todo esto viaja en texto plano, así que cualquiera que pueda ver el tráfico de la red lo puede leer.

## Riesgos encontrados

Si uso HTTP en un Wi-Fi público, alguien conectado a la misma red podría:

- Ver qué páginas visito.
- Ver datos de mi compu, como el navegador y el sistema operativo (por el User-Agent).
- Robar usuarios y contraseñas si las escribo en una página HTTP.
- Robar mis cookies y meterse en mis sesiones abiertas.
- Cambiar lo que veo en la página, por ejemplo para mandarme a un sitio falso.

## Cómo ayuda una VPN

Con una VPN pasan estas cosas:

- **Cifrado:** mis datos se vuelven ilegibles antes de salir de mi compu. Si alguien los intercepta, no entiende nada.
- **Túnel seguro:** la VPN encapsula mi tráfico y lo manda por un "túnel" cifrado hasta su servidor. Desde afuera solo se ve que me conecto a la VPN.
- **Protección del tráfico:** nadie en el Wi-Fi puede leer ni modificar lo que mando.
- **Privacidad:** los demás en la red no ven qué sitios visito.

Ojo: la VPN protege hasta su servidor. Si el sitio es HTTP, después de ahí sigue sin cifrar, así que igual conviene usar HTTPS.

## 3 Reglas de Oro

1. **Usar siempre HTTPS.** Fijarme que la página diga `https://` y tenga el candado.
2. **Usar una VPN** cuando me conecto a un Wi-Fi público.
3. **No poner datos importantes** (bancos, contraseñas) en redes públicas.
