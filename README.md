# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.1.6.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.1.6 - Manual.pdf` | El manual completo, 0 páginas con capturas. |
| `hyperpoc 0.1.6.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
2A49A5209253E4C3F10980C29431A2FB1209B8BF5A097C939F578D24A453301F
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.1.6.exe" SHA256
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
2. Doble clic en `hyperpoc 0.1.6.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.1.6

```
0.1.6 Beta  (13/08/2026)
  YA NO SE TE CUELA UNA ORDEN QUE NO TE CABE. Si metes una orden que pide mas de lo que tu
  cuenta puede abrir ahora mismo, NinjaTrader te lo dice ANTES y no la manda. Hasta ahora
  salia, la rechazaba Hyperliquid, y te enterabas despues: con sus palabras ("insufficient
  margin"), no con las tuyas, y con una orden a medias que habia que limpiar del grafico.

  El numero no nos lo inventamos: es el poder de compra que Hyperliquid dice que tienes, con
  tu saldo y tu apalancamiento ya dentro, y es EL MISMO que ves en el Control Center. Cada
  dex tiene el suyo, porque en Hyperliquid el dinero de cada uno es un bolsillo aparte.

  CERRAR Y REDUCIR NO SE BLOQUEAN NUNCA, ni con la cuenta a cero. Un stop y el boton Close no
  gastan margen: lo liberan. Quedarte encerrado dentro de una posicion porque el programa no
  te deja salir seria mucho peor que cualquier orden que se cuele.

  Y si no se puede comprobar (sin conexion, o Hyperliquid no publica el dato), la orden PASA
  y decide Hyperliquid. "No he podido mirarlo" no es "no tienes".

  LOS AVISOS YA TIENEN LA CARA DE NINJATRADER. Salian como cuadros de Windows: un recuadro
  blanco del sistema en mitad de una plataforma oscura, o al reves si usabas el tema claro.
  No era que estuvieran mal pintados: es que un cuadro del sistema no se puede pintar. Ahora
  son ventanas de NinjaTrader y toman el color del tema que tengas puesto, y ademas no
  bloquean la plataforma mientras estan abiertas.

  Lo mismo con las ventanas de Configurar, Apalancamiento, Historico y Acerca de: tenian los
  colores escritos a mano suponiendo el tema oscuro, asi que con el claro habia texto casi
  ilegible.

  TU ID DE INSTALACION, EN "ACERCA DE", con un boton para copiarlo. Es lo primero que hay que
  preguntarte cuando escribes con un problema, y hasta ahora no habia forma de dartelo.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

