# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.3.9.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.3.9 - Manual.pdf` | El manual completo, 71 páginas con capturas. |
| `hyperpoc 0.3.9.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
44A8050CFA38F9A22E19B64ABA5321834BDF88BED17024130D7962A1037C8D0B
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.3.9.exe" SHA256
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
2. Doble clic en `hyperpoc 0.3.9.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.3.9

```
0.3.9 Beta  (09/09/2026)
  MOVER UNA ORDEN YA NO PUEDE PROVOCAR UN REDIBUJADO DE LA PANTALLA. El programa vigila
  continuamente que las ordenes que ves en NinjaTrader sean las que de verdad tienes en
  Hyperliquid: quita las que alli ya no existen, y si Hyperliquid tiene alguna que no ves,
  reconstruye la pantalla desde cero para reflejarla.

  El problema estaba en como funciona mover una orden. Hyperliquid no la mueve: la cancela y
  coloca otra nueva, con otro numero. Si tardaba un momento en dejar de listar la vieja, el
  vigilante la tomaba por "una orden que Hyperliquid tiene y NinjaTrader no enseña" y
  reconstruia la pantalla entera sin necesidad. Ese numero esta muerto por definicion --lo
  acaba de retirar el propio programa al mover la orden-- y ahora se sabe.

  Y por dentro: toda esa comparacion estaba metida en el puente, donde para comprobar un solo
  caso hacian falta NinjaTrader abierto, conexion, ordenes reales y ademas conseguir que se
  descuadraran. Ahora esta aparte y se le hacen 24 preguntas en cada entrega, sin abrir el
  programa: la orden recien enviada que todavia no aparece, la que se ejecuto hace un segundo,
  la que esta a mitad de movimiento, y la que Hyperliquid tiene puesta desde la web.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

