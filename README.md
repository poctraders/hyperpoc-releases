# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.4.6.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.4.6 - Manual.pdf` | El manual completo, 73 páginas con capturas. |
| `hyperpoc 0.4.6.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
CC587F0CCD785CB39793EDAC08FD3C935A242AAD87A71D4BD0FCC0DFDC61CB0E
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.4.6.exe" SHA256
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
2. Doble clic en `hyperpoc 0.4.6.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.4.6

```
0.4.6 Beta  (17/11/2026)
  COMPATIBLE CON NINJATRADER 8.1.9.0, Y UN FALLO DE HORARIOS QUE SALIO AL PROBARLO.

  TUS GRAFICOS DE CRIPTO VUELVEN A SER DE 24 HORAS. En una instalacion nueva, los 704
  mercados se daban de alta con HORARIO DE BOLSA ESTADOUNIDENSE --de lunes a viernes, con su
  cierre por la tarde-- en vez de con el horario continuo que les toca. En la pantalla eso se
  ve como graficos que no pintan el fin de semana, cortes de sesion donde no deberia haberlos,
  y NinjaTrader tratando como cerrado un mercado que esta abierto.

  La causa: el horario 24/7 se copiaba de un instrumento de fabrica de NinjaTrader llamado
  BTCUSD, buscandolo por el nombre. NinjaTrader 8.1.9.0 reparte DOS instrumentos con ese
  nombre --uno de cripto y uno de CFD-- y se cogia el que salia primero, que ahora es el de
  CFD. Ahora no se busca por nombre: se busca un instrumento que REALMENTE tenga el horario
  de cripto, y si hay que cambiar de plantilla queda dicho en el registro.

  Si ya tenias hyperpoc funcionando, esto no te afectaba: el programa re-sincroniza los
  horarios cada vez que conecta, asi que los tuyos ya estaban bien. Afectaba a quien instala
  por primera vez, hasta la primera conexion.

  AHORA SE COMPRUEBA QUE NINJATRADER NO NOS HA CAMBIADO NADA. Buena parte de hyperpoc tiene
  que meter la mano en sitios de NinjaTrader que su propio manual no documenta --el cuadro de
  la cantidad, el selector de cuenta del grafico, las plantillas--. Si una version nueva les
  cambia el nombre, el programa no da ningun error: simplemente deja de poner la cantidad por
  defecto, o de leer la cuenta del grafico, sin decir nada. Se ha anadido una comprobacion que
  pregunta por cada una de esas piezas antes de dar una version por buena. En 8.1.9.0 estan
  todas.

  SI REINSTALAS NINJATRADER, HAY QUE REINSTALAR HYPERPOC. Una instalacion LIMPIA de
  NinjaTrader --no una actualizacion normal-- rehace su carpeta de documentos y se lleva por
  delante los tres componentes de hyperpoc, el motor y la configuracion, INCLUIDA TU CLAVE DE
  API. Hay que volver a instalar hyperpoc y volver a meter la clave en
  HyperPoc > Conexion > Configurar.

  Tu LICENCIA no se pierde: vive en el registro de Windows y una reinstalacion de NinjaTrader
  no la toca. No se te reinicia el periodo de prueba ni pierdes la activacion.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

