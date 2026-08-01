# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 1.1.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 1.1 - Manual.pdf` | El manual completo, 40 páginas con capturas. |
| `hyperpoc 1.1.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
704E5D5AEF8801E3E54CE010C38058995323BC9655BD16AE637DA0DE5222F20F
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 1.1.exe" SHA256
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
2. Doble clic en `hyperpoc 1.1.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 1.1

```
1.1  (01/08/2026)
  ARREGLADO, y no es cosmetico: el aviso que sale al conectar decia "Tu cuenta de
  Hyperliquid siguio operando SOLA con NinjaTrader desconectado". Esa frase afirmaba
  una causa que el programa no puede conocer, y el dia que se destapo era ademas
  FALSA: la cuenta habia ejecutado 17 ordenes con NinjaTrader cerrado y no las mando
  este programa -- las mando una SEGUNDA API wallet desde otro ordenador. Quien lo
  leyo entendio lo unico que se podia entender: que el programa operaba por su cuenta.
  Ahora el aviso dice lo que se sabe: QUE ejecuto Hyperliquid, que esto NO sale de
  aqui (con la conexion cerrada no sale ni una peticion), y las dos unicas cosas de
  las que puede venir -- ordenes que ya tenias puestas alli, u otro ordenador con
  permiso para firmar en tu cuenta.

  NUEVO: en cada conexion se te dice CUANTAS API wallets pueden firmar en tu cuenta.
  Una cuenta de Hyperliquid admite varias a la vez, cada una viviendo en un sitio
  distinto, y todas firman igual. Si hay mas de una, sale con sus nombres en Control
  Center > pestana Log. Tener dos es normal si usas dos ordenadores; lo que no es
  normal es enterarte el dia que ves un movimiento que no reconoces. Y si ahi aparece
  una que no es tuya, revocala: en Hyperliquid, More > API.

  NUEVO: "Acerca de", la ultima entrada del menu. El logotipo, el copyright, LA
  VERSION que estas usando y dos enlaces que se pulsan: www.poctraders.com y
  info@poctraders.com. La version no es adorno: es lo primero que hace falta saber
  para poder ayudarte, y hasta ahora habia que ir a buscarla a "Aplicaciones
  instaladas" de Windows.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

