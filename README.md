# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.4.2.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.4.2 - Manual.pdf` | El manual completo, 71 páginas con capturas. |
| `hyperpoc 0.4.2.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
0C11EA91B222B619FF7D73093690C3EABAB358AF0D03D21CF914A5F2989C2E63
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.4.2.exe" SHA256
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
2. Doble clic en `hyperpoc 0.4.2.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.4.2

```
0.4.2 Beta  (16/09/2026)
  SEIS ARREGLOS MAS DEL CAMINO DE LAS ORDENES. Tres los encontro un betatester operando y
  tres salieron de revisar a fondo el codigo. Cuatro de ellos podian costar dinero.

  MODIFICAR UNA ORDEN A MEDIO EJECUTAR YA NO REPONE LO YA EJECUTADO. Es el mas caro de
  todos. Cuando mueves una orden, Hyperliquid no la ajusta: la cancela y coloca otra del
  tamano que se le diga. El programa le mandaba el tamano ORIGINAL, no lo que quedaba vivo.
  Asi que mover una limitada de 30.000 $ llena por la mitad dejaba 30.000 $ vivos otra vez,
  con 15.000 $ ya en la posicion: el doble de exposicion de la que creias tener, sin un solo
  aviso. Ahora va lo que queda. Y el ajuste automatico de stops y objetivos, que tenia las
  ordenes a medio llenar excluidas, ya las tiene en cuenta.

  UNA ORDEN LLAMADA "CLOSE ALGO" YA NO CIERRA LA POSICION ENTERA. El boton Close del Chart
  Trader crea una orden llamada "Close", y esas cierran la posicion exacta sin mirar la
  cantidad. El programa aceptaba CUALQUIER nombre que empezara por Close -- y los nombres
  de orden los pone quien las manda: en una estrategia, "CloseLong" o "CloseSignal" son
  nombres corrientes. Una orden de 10 $ llamada asi cerraba una posicion de 500 $. Ahora el
  nombre tiene que ser exacto, y no se pierde nada: una salida del tamano de la posicion ya
  cierra igual de exacto por el camino normal.

  SI UN MOVIMIENTO NO LLEGA A HYPERLIQUID, AHORA TE ENTERAS. Habia cuatro formas de que
  mover una orden no llegara -- sin enlace con la orden de alla, sin precio valido, con un
  tamano que redondea a cero, o con la orden ya llena -- y las cuatro se quedaban en el
  registro. Tu arrastrabas el stop, lo veias donde lo habias puesto, y en Hyperliquid seguia
  donde estaba. Ahora las cuatro lo dicen en pantalla.

  Y SI UNA CANCELACION NO LLEGA, TAMBIEN. El programa mandaba la cancelacion y seguia sin
  mirar si Hyperliquid la habia aceptado; si el motor estaba caido, se tragaba el fallo. La
  orden desaparecia de NinjaTrader y en Hyperliquid seguia puesta, viva y lista para
  ejecutarse. Ahora se mira la respuesta, y si no se puede confirmar se avisa -- sin afirmar
  que sigue puesta, porque no se sabe: se te manda a mirarlo.

  CUANDO HYPERLIQUID RECHAZA UN STOP, EL AVISO YA NO MIENTE. Decia siempre "NO tienes esa
  posicion". Para una entrada rechazada es verdad; para un stop rechazado es falso, y falso
  por el lado que hace dano: la posicion sigue abierta y lo que no esta puesto es la
  proteccion. Leias que no tenias nada y lo que tenias era dinero expuesto sin stop. Ahora
  el aviso distingue las dos cosas.

  Y SI NINJATRADER VA A TROCEARTE LAS ORDENES, TE LO DICE AL CONECTAR. NinjaTrader tiene una
  opcion de simulador, "Enforce partial fills", que en vez de llenar una orden entera cuando
  el precio la toca la va llenando contra el volumen. Con tres contratos de un futuro son
  tres apuntes y es realista; aqui las cantidades son DOLARES, asi que una orden de 30.000 $
  son treinta mil lotes -- y acabas viendo miles de ejecuciones de un dolar para una sola
  orden. En Hyperliquid tu orden es UNA y se comporta con normalidad: lo que se trocea es lo
  que NinjaTrader ensena. El programa lo detecta y te dice donde se apaga. No se toca la
  configuracion de nadie: es una opcion legitima y hay quien la quiere.

  Y SI EL MOTOR QUE FIRMA LLEVA UNA CONFIGURACION VIEJA, AHORA SE DICE. El motor arranca y
  se para con NinjaTrader, pero si NinjaTrader se cierra mal -- un cuelgue, el Administrador
  de tareas -- el motor sobrevive, y al volver a abrir se reaprovecha el que ya estaba. Ese
  motor lleva cargada la configuracion que leyo al arrancar: si entre medias has cambiado tu
  API wallet o de red, seguiria con la de antes, con la conexion en verde y sin que nada lo
  dijera. Ahora se detecta al conectar y se te dice que cierres NinjaTrader del todo. No se
  bloquea nada: quedarte sin poder cerrar una posicion por un problema nuestro seria peor.

  Por dentro: una revision NUEVA de punta a punta con dinero real (tools\revision_total.ps1)
  que encadena abrir, proteger, sacar dos trozos, ampliar, mover y cerrar -- por los dos
  lados -- comprobando cada paso contra la API publica de Hyperliquid.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

