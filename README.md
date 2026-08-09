# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 1.4.2.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 1.4.2 - Manual.pdf` | El manual completo, 51 páginas con capturas. |
| `hyperpoc 1.4.2.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
9CFB0CBEE09098813BD1C6BA0E1ACC1A8EB9DF327535DBA75BCD6EE169DB39AF
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 1.4.2.exe" SHA256
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
2. Doble clic en `hyperpoc 1.4.2.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 1.4.2

```
1.4.2  (09/08/2026)
  EL MOTOR VUELVE A SABER DONDE ESTA. Si tienes la 1.4.1 y te funciona, NO te cambia nada
  al actualizar: en una instalacion normal las dos versiones miran exactamente la misma
  carpeta. Se corrige un fallo que hoy no puede darte la cara, pero que estaba puesto para
  darla el dia menos pensado.

  QUE PASABA. El motor averigua donde vive su instalacion mirando desde que carpeta se le
  ejecuta. Al compilarlo en un unico fichero (el blindaje de la 1.4), esa pregunta empezo a
  contestar la carpeta TEMPORAL donde el programa se descomprime al arrancar, y no la que
  el usuario tiene en disco. Como el instalador pone siempre la instalacion en el mismo
  sitio, el resultado seguia siendo correcto por casualidad -- pero una copia del motor
  colocada en cualquier otro sitio habria trabajado, sin decir ni una palabra, sobre la
  instalacion de Documentos.

  Y LO MISMO EN "DONDE ESTA INSTALADO". Ese acceso directo esta para contestar de un
  vistazo donde vive tu configuracion; en la 1.4 y la 1.4.1 el renglon "ejecutable" daba
  esa carpeta temporal, con un nombre distinto en cada arranque y borrada al salir. Ahora
  dice el fichero que tienes en disco, que es lo unico util cuando hay que mirar algo.

  COMO SE ENCONTRO. Arreglando la comprobacion que revisa lo que se entrega: hasta hoy
  examinaba un paquete distinto del que se publicaba, y en cuanto miro el bueno, salto.
  Desde ahora esa comprobacion es obligatoria para publicar: si no se ha pasado sobre el
  fichero exacto que se va a subir, no se sube.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

