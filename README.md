# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.2.1.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.2.1 - Manual.pdf` | El manual completo, 65 páginas con capturas. |
| `hyperpoc 0.2.1.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
6D0C2A83EEC5224B170038C409D3BA4DA74EF937096F87B187788353FF443404
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.2.1.exe" SHA256
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
2. Doble clic en `hyperpoc 0.2.1.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.2.1

```
0.2.1 Beta  (14/08/2026)
  YA NO TE ACUSA DE ALGO QUE NO HAS HECHO. Al abrir un grafico saltaba "esa cuenta no opera este
  instrumento" sin que hubieras tocado nada. Ese aviso es para cuando eliges a mano una cuenta
  que no puede operar el instrumento del grafico -- y ese "a mano" era una deduccion que durante
  los primeros segundos de un grafico es falsa: NinjaTrader rellena el desplegable de cuentas y
  elige por su cuenta mientras el grafico carga, y eso se ve igual que si lo eligieras tu.

  Ahora, mientras el grafico se esta colocando, la cuenta se corrige igual pero sin decirte que
  la elegiste tu. Si la cambias tu de verdad, con el grafico ya asentado, se te sigue explicando
  como siempre.

  EL MANUAL DICE CUANTO HISTORICO PUEDES CARGAR. Hyperliquid sirve como mucho 5.000 velas por
  peticion, asi que subir los "Days to load" del grafico no consigue mas de lo que hay. En el
  capitulo 15 hay una tabla con el maximo de cada temporalidad: 3,4 dias en 1 minuto, 17 dias en
  5 minutos, 52 en 15 minutos, 208 en horario y unos 13 anos en diario. Y por que los graficos
  de tick, rango o volumen no tienen historico de verdad.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

