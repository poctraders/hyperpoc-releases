# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 1.2.2.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 1.2.2 - Manual.pdf` | El manual completo, 48 páginas con capturas. |
| `hyperpoc 1.2.2.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
9FBE6FC57AFD0F4E75BB9272118B2BA427EC9EDA568F8AC0AAD9340F1AD26EB5
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 1.2.2.exe" SHA256
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
2. Doble clic en `hyperpoc 1.2.2.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 1.2.2

```
1.2.2  (02/08/2026)
  EL AVISO DE CADUCIDAD DEJA DE DAR LA LATA. Hasta ahora, la ventana emergente que
  recuerda que tu API wallet caduca salia al conectar durante los ULTIMOS 30 DIAS. Como
  una API wallet dura 180 dias, eso son decenas de arranques seguidos con el mismo
  cartel -- y un cartel que sale treinta veces se cierra sin leerlo, justo para que el
  dia que de verdad importa ya no lo lea nadie.

  AHORA: la ventana emergente sale SOLO cuando quedan 7 DIAS O MENOS (y sigue saliendo
  una sola vez por sesion). El resto del tiempo no interrumpe a nadie.

  Y PARA NO PERDER EL DATO, esta siempre a mano: "Acerca de" (la ultima entrada del menu
  Hyperliquid Poctraders) enseña ahora los dias que faltan, con la fecha exacta. En gris
  mientras hay margen; en ambar la ultima semana, con el recordatorio de renovarla; y en
  rojo si ya caduco o si Hyperliquid la revoco. La linea de la pestaña Log del Control
  Center sigue saliendo en CADA conexion, igual que antes.

  Esa ventana NO consulta nada al abrirse ni pide nada a la red: enseña lo que ya trajo la
  conexion en curso, asi que se abre al instante.

  Y SOLO CON LA CONEXION ABIERTA. Desconectado no enseña ninguna fecha: dice "conecta con
  Hyperliquid para ver cuanto le queda". La caducidad es un dato de Hyperliquid, no de este
  programa, y entre una sesion y otra puedes haber renovado o revocado la clave desde el
  movil, desde la web o desde otro ordenador. Una fecha vieja enseñada como si fuera de
  ahora es peor que no decir nada.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

