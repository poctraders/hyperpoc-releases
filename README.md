# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.2.3.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.2.3 - Manual.pdf` | El manual completo, 65 páginas con capturas. |
| `hyperpoc 0.2.3.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
90B8F119094E530A18BE41224D1338355186F4E8CC29B48CC86E3D014DD406D8
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.2.3.exe" SHA256
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
2. Doble clic en `hyperpoc 0.2.3.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.2.3

```
0.2.3 Beta  (17/08/2026)
  FUNCIONA CON NINJATRADER 8.1.8.2. Si acabas de actualizar NinjaTrader, esta es tu version.
  Todo lo que hacia la anterior sigue haciendolo: la conexion, las dos cuentas, el menu de
  mercados, los graficos con su plantilla y su cantidad, los indicadores y el historico.

  QUE SE HA COMPROBADO, porque "deberia funcionar" no es una comprobacion. NinjaTrader guarda
  muchas cosas en sitios que no forman parte de su manual, y este programa tiene que ir a
  buscarlas ahi: el desplegable de cuentas del grafico, la casilla de la cantidad, la carga de
  plantillas. Nada de eso da error si un dia cambia de nombre -- simplemente deja de hacer su
  trabajo, sin decir nada. Se han repasado uno a uno los diecinueve sitios de ese tipo que este
  programa usa, y ademas la base de datos de NinjaTrader: tus mercados y tus cuentas siguen
  donde estaban. La actualizacion de NinjaTrader no se lleva nada por delante.

  Y EL AVISO DE VERSION NUEVA YA NO DICE "AL DIA" CUANDO NO LO SABE. Habia dos situaciones en
  las que un ordenador dejaba de recibir avisos para siempre -- y las dos quedaban anotadas
  como si todo fuera bien, que era la unica pista que habia. Ahora se distinguen. Y publicar
  una version con un numero MENOR que el anterior, que es lo que crea esa situacion, ya no se
  puede hacer por descuido.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

