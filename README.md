# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.2.0.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.2.0 - Manual.pdf` | El manual completo, 64 páginas con capturas. |
| `hyperpoc 0.2.0.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
2A3CB36FAE47EB00A03B84004D90043B8AA136CD8C47E286F907C852CB33D546
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.2.0.exe" SHA256
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
2. Doble clic en `hyperpoc 0.2.0.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.2.0

```
0.2.0 Beta  (14/08/2026)
  LA LISTA DE MERCADOS SE MANTIENE SOLA. Hasta ahora los mercados se daban de alta una vez, al
  instalar, y ahi se quedaban. Hyperliquid lista y retira mercados continuamente, asi que a las
  pocas semanas tenias la lista de un exchange que ya no existia: faltaban los nuevos, y los
  retirados seguian dentro -- se podian graficar, y se podia intentar meter una orden en ellos
  para recibir a cambio un rechazo que no explicaba nada. Ninguno de los tres botones
  "Registrar..." quitaba nada; solo anadian.

  Ahora se pone al dia sola al conectar, y cada 6 horas si dejas NinjaTrader abierto. Solo se te
  avisa cuando la lista ha cambiado de verdad. Y con NinjaTrader desconectado no se pregunta
  nada a Hyperliquid, como siempre.

  PARA QUITAR UN MERCADO HAY QUE SABER, NO SUPONER. Que un mercado no aparezca puede ser que
  Hyperliquid lo haya retirado o que no se haya podido preguntar, y confundir las dos cosas
  borraria instrumentos que estan perfectamente vivos. Ahora el motor dice de que dexs ha
  podido leer de verdad, y solo se retira de ahi.

  Nunca se retira un mercado con posicion abierta, con una orden viva o con un grafico delante.
  Ni uno tuyo: solo se tocan los que dio de alta este programa. Y si de golpe sobraran decenas,
  no se toca nada y se dice: eso no es como retira mercados Hyperliquid, es un fallo nuestro
  leyendo. Puedes ver que haria sin que haga nada desde la ventana de mantenimiento
  ("Ver que cambiaria").

  Y ARREGLADO "REGISTRAR BUILDER", que llevaba roto sin que se notara. Contestaba "no se pudo
  leer del motor, esta arrancado?" -- y el motor estaba arrancado: lo que faltaba era la
  contrasena local en la peticion. Quien pulsara ese boton se quedaba sin los mercados de los
  dex builder (SP500, oro, acciones) y buscando el fallo donde no estaba.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

