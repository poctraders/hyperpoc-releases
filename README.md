# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.1.8.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.1.8 - Manual.pdf` | El manual completo, 54 páginas con capturas. |
| `hyperpoc 0.1.8.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
4F18ADCB67AB1E8F64DC9DC196ED2562C6ED1C77A426740CF0013CD698206E55
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.1.8.exe" SHA256
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
2. Doble clic en `hyperpoc 0.1.8.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.1.8

```
0.1.8 Beta  (14/08/2026)
  YA NO SE TE CUELA UNA ORDEN EN UN MERCADO QUE NO PUEDES OPERAR. En Hyperliquid, el dinero de
  cada dex es un bolsillo aparte: el saldo de tu cuenta principal no respalda posiciones de
  otro dex. Los mercados de un dex en el que no tienes cuenta se pueden VER en un grafico pero
  no operar, y el menu ya lo decia ("Otros dex - sin cuenta, solo grafico")... pero luego nadie
  lo impedia. La orden salia hacia un bolsillo con 0 $, Hyperliquid la aceptaba y la anulaba, y
  detras venia un aviso tras otro. Ahora se para antes de salir y se te dice por que.

  Las dos guardias que ya existian miraban a otro lado: la de cuenta comparaba con la cuenta
  que le tocaba al instrumento y no habia ninguna, asi que no comparaba nada; la de margen
  miraba el poder de compra de la cuenta desde la que metiste la orden -- la principal, que si
  tiene dinero -- cuando lo que iba a gastar era otro bolsillo.

  EL AVISO DE "NO SE HA MOVIDO LA ORDEN" YA NO TE MIENTE. Decia siempre lo mismo pasara lo que
  pasara: "en Hyperliquid sigue donde estaba" y "causa habitual: el minimo de 10 $". Cuando
  Hyperliquid contesta que esa orden ya esta ejecutada o cancelada, las dos cosas son falsas:
  alli no queda ninguna orden que pueda seguir en ningun sitio, y el tamano no ha tenido nada
  que ver. Se te pedia desconfiar de una linea del grafico que lo que necesitaba era irse.

  Ahora, cuando Hyperliquid dice que la orden ya no existe, se quita de NinjaTrader (alli no se
  toca nada) y solo se te avisa si tenias posicion abierta, que es cuando importa: acabas de
  quedarte sin esa proteccion.

  Y UN AVISO YA NO SALE SEIS VECES. Se llegaron a ver seis ventanas identicas apiladas tapando
  la plataforma. El fallo de fondo esta arreglado arriba, pero un aviso que puede salir N veces
  es un fallo por si mismo: nadie lee el sexto cuadro, se aprende a cerrarlos a ciegas, y el
  dia que uno diga algo distinto tampoco se leera. Si un aviso sigue en pantalla, no se abre
  otro igual. No se pierde nada: lo que no sale por pantalla queda en el registro.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

