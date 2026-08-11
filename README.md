# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 1.4.4.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 1.4.4 - Manual.pdf` | El manual completo, 51 páginas con capturas. |
| `hyperpoc 1.4.4.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
9E2B5AC35ED17F99D6F7C69CB600802ADEF399C4973AE13EE9933D45FDDB7BE4
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 1.4.4.exe" SHA256
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
2. Doble clic en `hyperpoc 1.4.4.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 1.4.4

```
1.4.4  (11/08/2026)
  EL APALANCAMIENTO YA ES EL DE HYPERLIQUID, TAMBIEN EN NINJATRADER. Hasta ahora NinjaTrader
  se comportaba como si todo fuera 1x: con 18,41 $ en la cuenta decia que tu poder de compra
  eran 18,41 $, cuando Hyperliquid te dejaba abrir 183,77 $ en BTC (a 10x) o 368,19 $ en ETH
  (a 20x). El numero era el saldo RETIRABLE, no lo que puedes abrir. Ahora se multiplica por
  tu apalancamiento de verdad.

  UN APUNTE HONESTO. Hyperliquid aplica el apalancamiento POR ACTIVO y NinjaTrader solo tiene
  UN poder de compra por cuenta, asi que hay que elegir un numero: se usa el MAS ALTO que
  tengas configurado en esa cuenta. Asi NinjaTrader no te frena nunca algo que Hyperliquid
  aceptaria. Si te pasas del tope del activo concreto, Hyperliquid la rechaza y el aviso de
  siempre te dice el motivo -- un error que se ve, en vez de uno que te desinforma callado.

  Y AHORA SE VE, EN TIEMPO REAL, JUNTO A LA ORDEN. En el grafico (al lado de la linea de
  liquidacion) y en el panel de ordenes aparecen tres cifras:
      x30 Cross  ·  360,00 $ en mercado  ·  12,00 $ de tu dinero  ·  libre para abrir: 192,00 $
  El multiplicador, lo que hay en mercado, cuanto de TU dinero lo sostiene y lo que aun
  puedes abrir. Estando plano tambien sale el "x30" y el "libre para abrir", que es cuando de
  verdad se mira: antes de entrar. Ninguna cifra se estima aqui -- el "libre para abrir" lo
  calcula Hyperliquid con tu saldo y tu apalancamiento, asi que coincide siempre con lo que
  te dejaria hacer.

  MENOS VENTANAS. El aviso de "se ha cerrado en Hyperliquid automaticamente" (1.4.3) ya no
  interrumpe: sale bien, no hay nada que hacer, y queda en el registro. El que SI sigue
  saliendo es el del caso malo -- si no se consigue cerrar, tienes dinero expuesto y hay que
  entrar a cerrarlo a mano.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

