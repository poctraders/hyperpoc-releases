# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.2.6.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.2.6 - Manual.pdf` | El manual completo, 65 páginas con capturas. |
| `hyperpoc 0.2.6.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
700CABD353B0E6649A7EFD802F331F2EEE26957A639299FF7E29EDCD006B0DF3
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.2.6.exe" SHA256
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
2. Doble clic en `hyperpoc 0.2.6.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.2.6

```
0.2.6 Beta  (18/08/2026)
  EL APALANCAMIENTO YA NO ENSANCHA EL PANEL DE ORDENES. En el Chart Trader, las cifras del
  instrumento iban todas en UNA linea seguida ("x10 Cross - 50,13 $ en mercado - 5,01 $ de tu
  dinero - libre para abrir: 183,35 $"), y esa frase estiraba a lo ancho la columna entera con
  la que se opera. Ahora va una cifra por renglon, con tres renglones reservados de alto: el
  rotulo crece hacia abajo y ya no puede deformar el panel. Ademas tiene un tope de ancho duro
  contra el selector de cuenta, asi que pase lo que pase con el texto, la columna se queda como
  esta.

  Y EL ALTO NO CAMBIA AL ABRIR O CERRAR UNA POSICION, que era lo otro que molestaba: como el
  hueco esta reservado, los botones de debajo dejan de moverse mientras operas.

  UN MENSAJE DEL REGISTRO QUE DECIA UNA COSA POR OTRA. Al segundo de una compra buena podia
  aparecer "el lado no coincide (NinjaTrader Long, Hyperliquid Short)" cuando Hyperliquid no
  estaba corto: es que todavia no tenia la posicion. No cambiaba nada de lo que hace el
  programa -- el aviso se descarta solo a los 45 s, y para eso esta --, pero un diagnostico que
  se inventa el lado de una posicion es peor que uno que dice "aun no lo se". Ahora lo dice.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

