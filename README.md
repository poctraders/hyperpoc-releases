# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 1.4.3.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 1.4.3 - Manual.pdf` | El manual completo, 51 páginas con capturas. |
| `hyperpoc 1.4.3.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
B06159678E125D5EC3CBB0ED0978E77D9DDB8E1AE4C3B7703D1AC5C9165B7F37
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 1.4.3.exe" SHA256
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
2. Doble clic en `hyperpoc 1.4.3.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 1.4.3

```
1.4.3  (11/08/2026)
  SI CIERRAS EN NINJATRADER, SE CIERRA EN HYPERLIQUID. ACTUALIZA. Podia pasar que tu stop o
  tu objetivo saltara, NinjaTrader te dejara la posicion PLANA, y en Hyperliquid siguiera
  ABIERTA. Con dinero dentro, su liquidacion corriendo, y tu creyendo que habias salido.

  POR QUE PASABA. Tu stop vive en dos sitios a la vez: en NinjaTrader, que lo dispara con el
  precio de su grafico, y en Hyperliquid, que lo dispara con SU precio de marca. No son el
  mismo numero. Casi siempre saltan a la vez y no se nota; cuando no, las dos plataformas se
  quedan contando cosas distintas.

  LO GRAVE NO ERA ESO, ERA EL SILENCIO. El programa tiene un vigilante que compara lo que
  tienes en NinjaTrader con lo que hay en Hyperliquid... pero solo miraba en una direccion:
  "NinjaTrader tiene algo que Hyperliquid no tiene". Al reves -- Hyperliquid con una posicion
  que NinjaTrader no enseña -- NO LO MIRABA NADIE. Ni un aviso, ni una linea en el registro.
  Solo se veia entrando en la web de Hyperliquid.

  QUE HACE AHORA, y son dos cosas distintas:
   · Si el cierre lo ha provocado NinjaTrader (salta tu stop, tu objetivo, o pulsas Close) y
     al comprobarlo Hyperliquid sigue abierta, SE CIERRA ALLI automaticamente y te lo dice.
     Espera unos segundos antes: lo normal es que Hyperliquid cierre sola, y adelantarse
     seria mandar un cierre por algo que iba a cerrarse igual. Si tras tres intentos no lo
     consigue, te avisa de que tienes dinero expuesto y que entres a cerrarlo a mano.
   · Si la posicion aparece en Hyperliquid sin que NinjaTrader la conozca (la abriste desde
     la web, o desde otro ordenador), NO SE CIERRA SOLA -- eso seria que el programa liquide
     algo que abriste queriendo. Se te avisa y NinjaTrader se repinta con lo que hay en
     Hyperliquid, que es la regla de siempre: manda Hyperliquid.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

