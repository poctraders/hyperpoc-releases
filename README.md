# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 1.4.5.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 1.4.5 - Manual.pdf` | El manual completo, 51 páginas con capturas. |
| `hyperpoc 1.4.5.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
73DF14CA32C3EA6D27B379B44A8CEF814EC319ED7570E4590096C66DB9AB6741
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 1.4.5.exe" SHA256
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
2. Doble clic en `hyperpoc 1.4.5.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 1.4.5

```
1.4.5  (11/08/2026)
  TUS INSTRUMENTOS BUILDER YA NO DESAPARECEN DEL MENU. Pasaba de vez en cuando al abrir
  NinjaTrader: entrabas en "Hyperliquid Poctraders > Instrumentos" y NO estaba la seccion de
  tu cuenta builder (XYZ y demas). Sus instrumentos no se perdian --seguian ahi, mezclados
  entre los del dex principal-- pero encontrarlos era imposible si no sabias buscarlos, y se
  quedaba asi TODA la sesion. La unica salida era descubrir "Actualizar lista".

  POR QUE. El menu se construye UNA sola vez, la primera que lo abres, y para saber de que
  cuenta es cada instrumento necesita unos datos que el motor tarda unos segundos en cargar.
  Si abrias el menu en esos primeros segundos, todo se colocaba bajo la cuenta principal --y
  ahi se quedaba, porque el menu ya se daba por construido--. Cuestion de tener el raton
  rapido: por eso pasaba unas veces si y otras no.

  AHORA. Si el menu se construye antes de tiempo, no se da por bueno: la proxima vez que lo
  abras se rehace solo, ya con todo en su sitio. No hay que tocar nada ni saber que existe
  "Actualizar lista" (que sigue estando, para forzarlo cuando quieras).
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

