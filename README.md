# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.2.5.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.2.5 - Manual.pdf` | El manual completo, 65 páginas con capturas. |
| `hyperpoc 0.2.5.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
A1DC90F78FB49D5F0D89B560C4AA82AA00B0923213D6F54F2C5ECB512720EAE3
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.2.5.exe" SHA256
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
2. Doble clic en `hyperpoc 0.2.5.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.2.5

```
0.2.5 Beta  (17/08/2026)
  EL APALANCAMIENTO VUELVE A CONTAR AL PONER UNA ORDEN. Con BTC puesto a x10, Hyperliquid
  dejaba abrir diez veces el saldo -- y NinjaTrader bloqueaba, sin llegar a enviarla,
  cualquier orden que pasara del saldo a secas. Desde fuera se ve como "el apalancamiento no
  hace nada y ademas no llega a Hyperliquid", y es literal: la orden ni salia de aqui.

  QUE PASABA. Hyperliquid pone el apalancamiento POR ACTIVO y NinjaTrader solo admite UN
  poder de compra por cuenta. Ese numero unico salia de los mercados que tuvieras EN
  PANTALLA; sin ningun grafico de ese mercado abierto no habia dato, se caia al saldo a
  secas -- o sea, la cuenta entera se comportaba como si fuera 1x -- y la guardia que evita
  las ordenes que no caben acababa frenando ordenes que Hyperliquid habria aceptado.

  QUE HACE AHORA. Antes de negarse pregunta por EL MERCADO DE LA ORDEN: cuanto deja abrir
  Hyperliquid ahi mismo, con tu saldo y con el apalancamiento que TU tienes puesto en ese
  activo. Es el mismo numero que ya ves junto a la orden de entrada como "libre para abrir",
  asi que lo que decide y lo que lees no pueden discrepar. Y solo pregunta cuando iba a
  frenar: si la orden cabe, no cuesta ni una llamada.

  Y SI NO PUEDE AVERIGUARLO, DEJA PASAR. No haber podido comprobar algo no es haber
  comprobado que no lo tienes: entonces decide Hyperliquid, que es quien manda de verdad.
  Cerrar y reducir no se frenan nunca, como siempre.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

