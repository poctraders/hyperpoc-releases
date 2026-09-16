# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.4.0.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.4.0 - Manual.pdf` | El manual completo, 71 páginas con capturas. |
| `hyperpoc 0.4.0.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
0E667E616BE6E535D04F8D8B5F05CBA5CF378A14A6767D4B11340615AB59946C
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.4.0.exe" SHA256
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
2. Doble clic en `hyperpoc 0.4.0.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.4.0

```
0.4.0 Beta  (16/09/2026)
  SACAR UN TROZO DE LA POSICION. Cerrarla entera funcionaba: el boton Close le pide a
  Hyperliquid que cierre la posicion EXACTA, y eso no falla nunca. Sacar solo una parte,
  no. Podia dejar la posicion en un tamano que no era el que tocaba, y en el peor caso
  abrir una posicion nueva del lado contrario. Arreglado, y por los dos lados.

  EN HYPERLIQUID. La cantidad que escribes en NinjaTrader son los DOLARES QUE METISTE,
  valorados al precio al que entraste. Al sacar un trozo a mercado, el programa convertia
  esos dolares a tamano con el precio de AHORA -- que ya no es el mismo -- y mandaba la
  orden sin decirle a Hyperliquid que solo podia CERRAR. Con el precio en contra, esa
  cuenta se pasaba de la posicion entera: la cruzaba y abria la contraria. Sacar "los
  200 $ que meti" de una posicion larga que habia bajado un 10 % dejaba un corto.

  Ahora una salida a mercado le dice a Hyperliquid QUE FRACCION de la posicion quieres
  sacar, y el tamano lo pone Hyperliquid contra tu posicion real. La mitad es la mitad.
  Y va marcada como de solo cierre: no puede abrir nada, pase lo que pase con el precio.
  Es el mismo mecanismo que ya usaban el stop y el objetivo desde hace meses.

  EN NINJATRADER. Si tenias 200 $ con un stop de 200 $ y sacabas 100 $, te quedaba la
  posicion en 100 $ y el stop en 200 $. El dia que saltaba ese stop, NinjaTrader vendia
  los 200 contra los 100 que quedaban y te dejaba CORTO de 100 $ -- una posicion que no
  habias pedido. En Hyperliquid eso no llegaba a pasar (alli el stop es de solo cierre y
  se para en tu posicion), asi que las dos pantallas acababan contando cosas distintas y
  el programa terminaba reconstruyendo la suya.

  Ahora, en cuanto la posicion mengua, el stop y el objetivo se ajustan solos a lo que
  queda. No pierdes proteccion: se quedan exactamente en la cifra que Hyperliquid iba a
  ejecutar de todas formas. Y las ordenes de REVERSION -- las que pones a proposito mas
  grandes que la posicion para darle la vuelta de un golpe -- se quedan como estan: esas
  si pueden abrir, y para eso las pusiste.

  Por dentro: las dos decisiones estan fuera del puente y se les hacen 46 preguntas en
  cada entrega, sin abrir el programa ni gastar un centimo. Y una mas en vivo, con dinero
  de verdad: abrir 24 $, ponerle stop y objetivo, sacar 12 $ y comprobar contra la propia
  Hyperliquid que los tres numeros se quedan en 12.

  TU LICENCIA SE GESTIONA EN UN SOLO SITIO: HyperPoc > Acerca de. Alli esta el estado de
  tu licencia, el boton para meter una clave nueva o quitar la que tengas, y tu ID de
  instalacion con su boton de copiar. Habia un segundo boton de licencia dentro de
  Conexion > Configurar, y no pintaba nada ahi: con que wallet firmas en Hyperliquid y
  que licencia tienes de HyperPoc son dos cosas que no se parecen en nada, y verlas
  juntas hacia pensar que configurar la conexion era un tramite de tres pasos. Ese boton
  se ha quitado; la ventana de conexion es ahora lo que dice ser.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

