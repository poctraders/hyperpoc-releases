# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.4.3.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.4.3 - Manual.pdf` | El manual completo, 73 páginas con capturas. |
| `hyperpoc 0.4.3.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
AD374CC1127300A552539E09DED17E0550DC0AD87B9E45D82A0B03FED70D71CB
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.4.3.exe" SHA256
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
2. Doble clic en `hyperpoc 0.4.3.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.4.3

```
0.4.3 Beta  (16/09/2026)
  LOS AVISOS DE ORDEN RECHAZADA YA DICEN DE QUIEN ES EL RECHAZO. Habia dos clases mezcladas
  bajo el mismo rotulo, y eso hacia que el programa se contradijera solo.

  Los codigos HL-xx traducen lo que ha contestado HYPERLIQUID. Pero hay ordenes que el
  programa se niega a mandar EL MISMO, sin llegar a tocar el cable: una vigencia que
  Hyperliquid no tiene, un importe que redondea a cero, un tipo de orden que no sabe
  traducir. Esas salian rotuladas "HL-00", que es justamente el codigo de "Hyperliquid ha
  dicho algo que no se traducir". O sea: el titulo declaraba no entender un rechazo que el
  propio programa acababa de escribir tres lineas mas arriba, y de paso daba a entender que
  el exchange habia dicho algo cuando ni se le habia preguntado.

  Y UNA ORDEN QUE NO CUAJA YA NO TE RECONSTRUYE LA PANTALLA. Una orden IOC que no encuentra
  contrapartida no es un fallo: es lo que significa IOC -- o entra en el momento, o no queda
  nada. Pero el programa lo trataba como "no se que tiene Hyperliquid" y reconstruia el
  simulador entero: te cancelaba y recreaba TODAS las ordenes, dejando un momento en el que
  tus protecciones no estaban en pantalla. Por una IOC, que es justo el tipo de orden que se
  usa a proposito sabiendo que a veces no va a entrar. Ahora, cuando lo unico fuera de sitio
  es esa orden, se quita esa orden y nada mas; solo se reconstruye cuando de verdad hace
  falta, que es cuando ha quedado una posicion que en Hyperliquid no existe.

  Ahora esas llevan su propia serie, HP-01 a HP-07, y el aviso se titula "la orden no se ha
  enviado" en vez de "rechazada" -- que es lo que ha pasado de verdad. En el manual estan las
  dos tablas, una al lado de otra: HL para lo que dice Hyperliquid, HP para lo que decidimos
  aqui. Si escribes por un rechazo, el codigo sigue siendo lo unico que hace falta mandarnos.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

