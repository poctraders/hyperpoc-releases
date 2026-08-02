# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 1.3.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 1.3 - Manual.pdf` | El manual completo, 0 páginas con capturas. |
| `hyperpoc 1.3.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
E0DB6462496BC673F0FD95100A46D5C0EE1FA4F2F440D98987C5764833F95F75
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 1.3.exe" SHA256
```

Tiene que dar exactamente ese número. Si no coincide, el archivo no es el que salió de aquí:
bórralo y vuelve a descargarlo.

---

## Antes de instalar

- Windows 10 u 11, 64 bits.
- **NinjaTrader 8** instalado y abierto al menos una vez (hasta que no lo abres no crea su
  carpeta de datos y no hay dónde instalar nada).
- Una cuenta de Hyperliquid con fondos.
- Una **API wallet** de Hyperliquid (en la web: *More → API*). Es la clave que firmará tus
  órdenes: **firma pero no puede retirar fondos**. Nunca la clave principal de tu cartera — el
  programa la detecta y se niega a guardarla.

> **Apunta la clave en el momento de crearla.** Hyperliquid la enseña una sola vez y no hay
> forma de volver a verla.

## Instalar

1. **Cierra NinjaTrader.**
2. Doble clic en `hyperpoc 1.3.exe`. Windows mostrará una pantalla azul porque el archivo no
   está firmado con un certificado comercial: *Más información* → *Ejecutar de todas formas*.
   Pedirá permisos de administrador **una vez**.
3. Abre NinjaTrader. Cuando pregunte si autoriza los complementos, responde **Sí**.
4. `Control Center → Hyperliquid Poctraders → Conexión → Configurar…` y mete tu cuenta.
   Pulsa **Comprobar** antes de guardar.
5. `Conexión → Conectar`.

Para **actualizar**, instala la versión nueva encima con NinjaTrader cerrado. No hay que
desinstalar nada ni volver a meter la clave.

Todo lo demás —campo por campo, ventana por ventana— está en el manual.

---

## Avisos honestos

- Esto usa **dinero real** desde el primer momento. No tiene modo de prácticas. Empieza con
  importes pequeños; Hyperliquid rechaza por debajo de 10 $.
- **No es un robot**: no decide, no entra y no sale por su cuenta.
- **No custodia tu dinero**: firma órdenes, y no puede retirar nada.
- **No deja nada corriendo.** Ni servicio, ni tarea programada, ni proceso al iniciar sesión:
  mientras no conectes, no sale ni una petición hacia Hyperliquid. A cambio no hay avisos en el
  momento — si te salta un stop de madrugada, te lo cuentan la próxima vez que conectes.
- Las API wallets de Hyperliquid **caducan**. El programa te dice cuánto les queda cada vez que
  conectas.

## Novedades de la 1.3

```
1.3  (02/08/2026)
  TE AVISA CUANDO HAY UNA VERSION NUEVA. Hasta ahora, enterarse dependia de que a alguien
  se le ocurriera mirar la pagina de descargas. El 01/08/2026 ya paso: un ordenador con la
  0.2.1 y otro con la 1.2, meses de arreglos de diferencia, y nada en pantalla que lo
  dijera. Un fallo ya corregido que te sigue pasando porque nadie te dijo que estaba
  corregido es un fallo que sigue vivo.

  COMO FUNCIONA: al abrir NinjaTrader, UNA vez por sesion y en segundo plano, se le
  pregunta a GitHub cual es la ultima version publicada. Si la tuya es mas vieja, sale una
  ventana con la version que tienes, la que hay, un enlace "pincha aqui" y tres salidas:

    · Descargar ahora        abre la pagina de descargas y CIERRA NinjaTrader (el
                             instalador no puede sustituir los ficheros con NT abierto).
                             Tus posiciones y ordenes NO se tocan: viven en Hyperliquid.
    · Recordarmelo mas tarde no anota nada; vuelve a salir en el proximo arranque.
    · Descartar esta version no vuelve a mencionar ESA. Si sale una posterior, si avisa:
                             descartar una version no es apagar el aviso para siempre.

  LO QUE **NO** HACE: no descarga ni ejecuta nada. Abre la pagina en tu navegador y ya.
  Un instalador de 21 MB bajado y lanzado solo, sin que nadie vea de donde viene ni
  compruebe el hash, es justo la comodidad por la que luego se cuelan cosas. Bajas tu,
  comparas el SHA256 que anuncia la pagina y ejecutas tu.

  SI NO HAY RED, O GITHUB NO CONTESTA: no sale nada. Ni un aviso, ni un error. Queda
  anotado en el registro y punto. Una ventana de "no he podido comprobar si hay
  actualizaciones" es ruido que no puedes accionar, y encima entrena a cerrar las ventanas
  de esta aplicacion sin leerlas -- que es lo que se acaba de arreglar en la 1.2.2 con el
  aviso de caducidad.

  Esta consulta va a GitHub, NO a Hyperliquid: abrir NinjaTrader sigue sin conectar con el
  exchange ni tocar tu cuenta.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

