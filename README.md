# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.3.6.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.3.6 - Manual.pdf` | El manual completo, 68 páginas con capturas. |
| `hyperpoc 0.3.6.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
594F630833035E64C31AD96B1DBB5B7E1246957BD69DB2B316D3FE9D74F8582D
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.3.6.exe" SHA256
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
2. Doble clic en `hyperpoc 0.3.6.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.3.6

```
0.3.6 Beta  (04/09/2026)
  YA PUEDES CAMBIAR TU CLAVE SIN SALIR DEL PROGRAMA. En Hyperliquid Poctraders > Acerca de...
  hay un boton nuevo, "Renovar clave". Abre la caja donde pegar una clave: sirve para meter
  una nueva, para volver a poner la de siempre, o para QUITAR la que tengas. Hasta ahora la
  unica puerta estaba escondida en Conexion > Configurar..., o aparecia sola cuando el
  programa ya te estaba frenando: para meter una clave habia que tener un problema.

  QUE PASA SI QUITAS LA CLAVE. El programa vuelve a la prueba gratuita con LOS DIAS QUE TE
  QUEDARAN de tus 14 originales, no con catorce nuevos. Si esa prueba ya se agoto, el
  ordenador queda en solo lectura: puedes cerrar posiciones, reducirlas y cancelar ordenes
  -- eso no se bloquea nunca -- pero no abrir posiciones nuevas. Quitarla pide dos clics, y
  el primero te dice exactamente lo que va a pasar antes de hacerlo.

  Y si algo impidiera quitarla del todo, el programa NO te dice que la ha quitado: te avisa
  de que el ordenador puede seguir abierto. Un "hecho" que no es verdad es peor que un fallo.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

