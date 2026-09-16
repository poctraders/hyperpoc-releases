# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.4.1.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.4.1 - Manual.pdf` | El manual completo, 71 páginas con capturas. |
| `hyperpoc 0.4.1.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
CB638A393D5B854F091AAE7317F9311B825E69C6FC2A8EBED756C73A58686202
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.4.1.exe" SHA256
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
2. Doble clic en `hyperpoc 0.4.1.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.4.1

```
0.4.1 Beta  (16/09/2026)
  SEIS ARREGLOS DEL CAMINO DE LAS ORDENES, salidos de revisar el codigo caso por caso.
  Tres de ellos podian costar dinero.

  TU STOP YA NO PUEDE SALIR SIN PROTECCION. Cuando una estrategia ATM coloca el stop y el
  objetivo, lo hace en el mismo instante en que se llena la entrada -- y NinjaTrader tarda
  unos milisegundos en dar la posicion por abierta. En ese hueco el programa miraba, veia
  la cuenta plana, y mandaba el stop SIN la marca de "esto solo puede cerrar". Un stop asi,
  si salta cuando ya has sacado un parcial, no se para: abre la posicion contraria. Ahora
  la posicion se mira DOS veces, la segunda justo antes de enviar, y basta que una de las
  dos la vea para tratar la orden como lo que es.

  Y LO MISMO AL CAMBIARLE LA CANTIDAD A UN STOP. Si una ATM baja su stop porque acaba de
  llenarse un objetivo parcial, el programa calculaba la parte a cubrir con la posicion de
  antes: el stop acababa cubriendo la mitad de lo que quedaba, sin decirlo. Mismo arreglo,
  misma segunda mirada.

  VARIAS SALIDAS QUE JUNTAS NO CABEN. Dos objetivos escalonados de 16 $ sobre una posicion
  de 24 $ caben por separado y no juntos; si llenaban los dos, NinjaTrader vendia 32 contra
  24 y te dejaba corto de 8 sin que lo hubieras pedido. Ahora se mira tambien la SUMA -- y
  con cuidado: un stop y su objetivo se cancelan entre ellos, asi que cuentan una sola vez.
  Una ATM de dos objetivos bien puesta no se toca.

  EN SPOT YA NO SE PUEDE VENDER LO QUE NO TIENES. El mecanismo que reparte la posicion al
  sacar un parcial solo funciona en perpetuos: en spot no hay posiciones que consultar, asi
  que el tamano lo ponia una conversion al precio de AHORA, que ya no es el de tu entrada.
  Ahora la salida lleva las mismas unidades que NinjaTrader se esta quitando, y ademas se
  recorta al saldo que de verdad tienes: una orden de mas era un rechazo de Hyperliquid con
  NinjaTrader dandola ya por hecha.

  AMPLIAR UNA POSICION YA NO REDIBUJA LA PANTALLA SIN MOTIVO. El programa compara lo que ve
  NinjaTrader con lo que tiene Hyperliquid y, si no cuadran, reconstruye la pantalla. Entre
  las dos cuentas hay siempre un redondeo por CADA orden, y el margen solo daba para uno:
  al ampliar una posicion en dos o tres entradas los redondeos se sumaban y el margen no,
  asi que saltaba un descuadre que no existia -- con su reconstruccion detras, en mitad de
  la operativa. Ahora el margen crece con las ordenes que han construido la posicion, con
  tope, para no dejar de ver un llenado parcial de verdad.

  Y CUANDO HYPERLIQUID RECHAZA POR LA VIGENCIA, AHORA SE DICE DONDE SE ARREGLA. Hyperliquid
  solo admite GTC e IOC, y muchas plantillas de NinjaTrader traen "Day" de fabrica: con eso
  puesto no sale NI UNA orden. El aviso explicaba la causa pero no el gesto; ahora dice
  exactamente que desplegable hay que tocar, y avisa de que si se repite en todas las
  ordenes es que la plantilla viene asi.

  Dos sospechas mas se revisaron y resultaron NO serlo, y queda dicho aqui porque el
  proximo que mire no tenga que volver a mirarlo: el vinculo entre un stop y su objetivo
  sobrevive al ajuste automatico (comprobado en vivo), y un take-profit limitado puesto
  desde la web de Hyperliquid recupera su limite al reconectar.

  Por dentro: 122 preguntas en seco entre las nueve suites, dos mandos de prueba nuevos
  para poder volver a medir el caso del OCO, y la regresion en vivo del parcial repetida
  sobre esta version.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

