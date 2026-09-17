# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.4.4.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.4.4 - Manual.pdf` | El manual completo, 73 páginas con capturas. |
| `hyperpoc 0.4.4.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
AF62E646BAA837D2B4F566E2CDABE614F72B8998EA4DC74EDCA96EE197656550
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.4.4.exe" SHA256
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
2. Doble clic en `hyperpoc 0.4.4.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.4.4

```
0.4.4 Beta  (17/09/2026)
  TRES FALLOS QUE COSTABAN DINERO, Y UNA VENTANA QUE SE SALTABA TODAS LAS GUARDIAS.

  UNA ORDEN A MEDIO LLENAR YA NO TE RECONSTRUYE LA PANTALLA. Es el peor de los tres. El
  vigilante que compara tus ordenes con las de Hyperliquid no miraba las ordenes A MEDIO
  EJECUTAR: para el, esa limite tuya llena por la mitad sencillamente no existia. Pero en
  Hyperliquid si existe, con el resto descansando. Asi que la daba por "una orden que
  Hyperliquid tiene y NinjaTrader no enseña" y, al minuto, RECONSTRUIA EL SIMULADOR ENTERO:
  cancelaba y recreaba todas tus ordenes, con ese momento en el que tus protecciones no
  estan en pantalla. Por una orden a medio llenar -- que, como dijo un betatester, es una
  cosa bastante comun. Ahora cuenta como lo que es: una orden.

  UNA SALIDA YA NO PUEDE CONVERTIRSE EN UNA ENTRADA. Cuando el motor no conseguia calcular
  el tamaño de una salida contra tu posicion real, se limitaba a mandarla por el camino
  normal -- que no lleva la marca de "esto solo puede reducir". Resultado: en vez de cerrar,
  ABRIA. Pasaba en tres sitios, y en los tres Hyperliquid habia contestado con claridad:
  cuando alli ya no hay posicion (abria una nueva desde cero), cuando la posicion va al
  reves de lo que cree NinjaTrader (la agrandaba en vez de cerrarla), y cuando el trozo que
  pedias es mas pequeño que el minimo del activo (mandaba mucho mas de lo que querias sacar).
  Ahora esos tres casos se contestan con un rechazo claro y NO se manda nada. Si el motor
  simplemente NO PUEDE leer tu posicion, todo sigue como antes: no poder leer no es lo mismo
  que no haber, y quedarse sin poder salir del mercado seria peor.

  LA VENTANA "HYPERLIQUID TRADER" PASA POR LAS MISMAS REGLAS QUE EL GRAFICO. Esa ventana
  habla con Hyperliquid directamente, que es lo que la hace util para operar sin grafico --
  y era tambien lo que la dejaba fuera de todos los controles. Se podia abrir posicion desde
  ella con la licencia caducada mientras el Chart Trader estaba en solo lectura. Ahora se
  comprueba igual, con la misma excepcion de siempre: CERRAR y CANCELAR no se frenan nunca.
  Ademas el tamaño que escribes ya se valida como numero antes de salir, y el rotulo dice lo
  que hacia falta decir: ahi el tamaño va en CRIPTO (0,001 BTC), no en dolares como en el
  grafico. Es el unico sitio del programa donde conviven las dos unidades.

  Y LO QUE VIAJA AL MOVER UNA ORDEN MEDIO EJECUTADA queda comprobado de forma permanente.
  Ese arreglo entro en la 0.4.2 y no se habia podido ejercer nunca: para que el simulador
  deje una orden a medias, la orden tiene que ser mas grande que el volumen que imprime el
  mercado, y con ordenes de 36 $ cualquier operacion de BTC la cubre entera. Con los 30.000 $
  del betatester es el caso normal. Ahora esa cuenta se comprueba en seco, caso por caso.

  Comprobado con dinero real: los avisos de "no se ha podido cancelar", "no se ha movido la
  orden" y "el motor lleva la configuracion de antes" se han provocado a proposito y los tres
  avisan. 149 comprobaciones automaticas sin fallos.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

