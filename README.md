# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 1.2.1.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 1.2.1 - Manual.pdf` | El manual completo, 48 páginas con capturas. |
| `hyperpoc 1.2.1.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
68898BAB5C425D974ECCA3BED4BD981959242A56B7B05CC442325BA445F3EF97
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 1.2.1.exe" SHA256
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
2. Doble clic en `hyperpoc 1.2.1.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 1.2.1

```
1.2.1  (02/08/2026)
  PRIMERA VERSION DE TRES DIGITOS, y es a proposito: el tercer digito significa "cambio
  menor". El programa es EL MISMO que la 1.2 -- mismo motor, mismos complementos, mismo
  comportamiento. Lo que cambia esta entero en el manual.

  NUEVO EN EL MANUAL: un apendice A, "Ordenes y apalancamiento", que contesta desde cero
  la pregunta que mas dinero cuesta equivocar: cuando escribo 12 y le doy a comprar,
  cuanto dinero estoy metiendo de verdad. Explica que aqui la cantidad son DOLARES y no
  contratos ni lotes; por que hay un minimo de 10 $; por que a veces pides 12 $ y entran
  11,68 $ o 14,99 $ (el escalon de cada mercado, con una tabla de diez mercados reales);
  y sobre todo el malentendido caro: EL APALANCAMIENTO NO MULTIPLICA TU ORDEN. Poner x4
  no convierte 12 $ en 48 $ -- lo que hace es retener menos fianza y subirte el techo.
  Lleva tablas de apalancamiento maximo por mercado de las dos cuentas (cripto por un
  lado; bolsa, indices, divisas y materias primas por otro), la diferencia entre Cross e
  Isolated, tres ejemplos completos y una chuleta final.

  SI VIENES DE LA 1.2: no hace falta que instales nada para leerlo -- el manual en PDF se
  descarga suelto desde la pagina de descargas. Si aun asi instalas, se instala encima
  sin tocar tu configuracion ni tu clave.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

