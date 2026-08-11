# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.1.4.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.1.4 - Manual.pdf` | El manual completo, 51 páginas con capturas. |
| `hyperpoc 0.1.4.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
EECB65C2D67FC0DB35D3E9921474F16DFABF9B3C6C2E3550588B0BB93641E4E7
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.1.4.exe" SHA256
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
2. Doble clic en `hyperpoc 0.1.4.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.1.4

```
0.1.4 Beta  (11/08/2026)
  EL PODER DE COMPRA YA BAJA CUANDO BAJAS EL APALANCAMIENTO. En la 0.1.1 se estreno el poder
  de compra con apalancamiento real, y estaba mal de dos formas que se sumaban: ponias
  XYZ100 a 1x, el grafico decia "libre para abrir 8,87 $"... y el Control Center seguia
  diciendo 484,79 $. Reiniciando NinjaTrader, tambien.

  POR QUE. Se multiplicaba tu saldo por "el apalancamiento mas alto de la cuenta", y ese
  numero se guardaba en disco sin caducidad. Asi que el 50x de otro instrumento tapaba al
  1x del que estabas mirando, y encima el valor sobrevivia al reinicio. Un numero de riesgo
  que NO baja cuando bajas el riesgo es de lo peor que puede enseñar un programa.

  AHORA el numero lo da Hyperliquid: es lo que ella misma dice que puedes abrir, ya con tu
  saldo y tu apalancamiento dentro. No se calcula ni se recuerda nada. Cambias el
  apalancamiento y el Control Center cambia contigo, diciendo lo mismo que el grafico.

  Con varios graficos abiertos a distinto apalancamiento, NinjaTrader solo admite UN numero
  por cuenta: se queda con el mayor, para no frenarte una orden que Hyperliquid si aceptaria.
  Sin ningun grafico abierto enseña tu saldo retirable, que es lo honesto mientras no hay
  con que compararlo, y se corrige solo en cuanto abres uno.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

