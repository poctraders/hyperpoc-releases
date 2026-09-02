# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.3.5.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.3.5 - Manual.pdf` | El manual completo, 68 páginas con capturas. |
| `hyperpoc 0.3.5.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
4A9A9F25CB0777CB57E7F251B24BC37692AED82EA955E705EC500FA2EFE3B112
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.3.5.exe" SHA256
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
2. Doble clic en `hyperpoc 0.3.5.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.3.5

```
0.3.5 Beta  (03/09/2026)
  UNA POSICION QUE NO EXISTE YA NO PUEDE PASAR DESAPERCIBIDA. El programa vigila que lo que
  ves en NinjaTrader sea lo que de verdad tienes en Hyperliquid, y avisa (y lo corrige) si no
  cuadra. Ese vigilante tenia un punto ciego: cuando el mercado tenia un grafico abierto -o
  sea, justo cuando lo estas operando-, una posicion de VENTA que en Hyperliquid ya no existia
  podia quedarse en pantalla sin que nadie dijera nada. Con sus stops encima, protegiendo algo
  que no esta. Corregido: una posicion que no esta se dice que no esta, se vea el grafico o no.

  Dos arreglos mas en el mismo vigilante:
  - el aviso solo salta si el descuadre es EL MISMO durante 45 segundos seguidos. Antes dos
    descuadres pasajeros distintos podian sumarse y disparar una correccion que no tocaba;
  - cuando Hyperliquid tiene una posicion que NinjaTrader no muestra y no da el precio de
    entrada, el aviso decia "una posicion de 0,00 $". Ahora dice el tamano de verdad.

  Y por dentro: toda esa comparacion estaba metida en el puente, donde para comprobar un solo
  caso hacia falta NinjaTrader abierto, conexion, dinero y ademas conseguir que se descuadrara.
  Ahora esta aparte y se le hacen 34 preguntas en cada entrega, sin abrir el programa y sin
  gastar un centimo: el llenado parcial, el mercado que no se ha podido leer, la posicion
  abierta desde la web con NinjaTrader plano.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

