# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 1.4.1.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 1.4.1 - Manual.pdf` | El manual completo, 51 páginas con capturas. |
| `hyperpoc 1.4.1.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
F93F0F57728F15E2784573D90F108E987BA1E353FD029D89ED5D6E3728D8EE10
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 1.4.1.exe" SHA256
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
2. Doble clic en `hyperpoc 1.4.1.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 1.4.1

```
1.4.1  (09/08/2026)
  ARREGLA UNA 1.4 QUE NO PODIA OPERAR. Si tienes la 1.4, ACTUALIZA: al meter la clave de la
  API wallet contestaba "esa clave no es una clave privada valida" aunque la clave fuera
  perfecta, y tampoco llegaba a conectar. No era tu clave ni tu cuenta: al blindar el motor
  Python en la 1.4 se quedo fuera del ejecutable una pieza de criptografia (la que calcula
  keccak), y sin ella no se puede sacar la direccion de una clave ni firmar una orden. La
  pieza se elige sobre la marcha, en tiempo de ejecucion, y el compilador que blinda el
  programa no la vio venir.

  QUE TIENES QUE HACER: instalar esta version encima. NO vuelvas a meter la clave -- sigue
  guardada y cifrada donde estaba -- y NO tienes que crear ninguna API wallet nueva. Si
  llegaste a crear varias probando, puedes revocar las que te sobren en Hyperliquid
  (More -> API); no hace falta para que esto funcione.

  Y PARA QUE NO SE REPITA. El programa lleva ahora una autoprueba de firma con un resultado
  conocido, y la construccion de cada version la ejecuta contra el ejecutable ya compilado:
  si no firma, NO SE GENERA INSTALADOR. Se puede lanzar a mano con
  "hl_sidecar.exe --autoprueba" (no toca tu configuracion ni sale a la red). Ademas, cuando
  algo del motor falle, se dira que ha fallado el motor: la 1.4 presentaba una averia suya
  como si el dato que habias escrito estuviera mal, que es la peor forma de fallar --
  manda a buscar el problema justo donde no esta.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

