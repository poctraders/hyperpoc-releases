# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.4.5.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.4.5 - Manual.pdf` | El manual completo, 73 páginas con capturas. |
| `hyperpoc 0.4.5.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
79359B20F60783BE6ADB8F695CC673D64FCF14E245BDC119243804C5C86E3507
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.4.5.exe" SHA256
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
2. Doble clic en `hyperpoc 0.4.5.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.4.5

```
0.4.5 Beta  (17/09/2026)
  TUS PROTECCIONES SE AJUSTAN OCHO VECES MAS RAPIDO DESPUES DE UN PARCIAL, Y LA CARRERA DE
  LAS ATM SE HA PODIDO PROBAR POR FIN.

  DE 24 SEGUNDOS A 3. Cuando sacas un trozo de tu posicion, el stop y el objetivo que quedan
  son mas grandes que lo que te queda abierto, y el programa los recorta solo. Ese recorte
  tardaba hasta 24 segundos, y el motivo era que habia heredado una espera que no le tocaba:
  el vigilante que compara tus ordenes con Hyperliquid espera 20 segundos despues de cada
  envio, porque mover una orden alli la cancela y crea otra, y ese viaje puede durar. Pero el
  recorte no compara nada con Hyperliquid: compara dos numeros de NinjaTrader, el tamaño de
  tu posicion y el de tu orden, y ninguno de los dos depende de lo que este viajando.

  En Hyperliquid esas protecciones son reduce_only y nunca pudieron hacer daño --alli solo
  cerrarian lo que hay--. El riesgo estaba en el simulador de NinjaTrader: si el stop saltaba
  en ese hueco, vendia de mas y te dejaba la posicion del reves. Justo cuando el mercado
  corre, que es cuando un stop salta despues de un parcial. Medido antes y despues con la
  misma secuencia: 24 segundos antes, 3 ahora.

  LA CARRERA DE LAS ATM, PROBADA POR PRIMERA VEZ. Era el unico caso de la lista de pruebas
  que se daba por imposible de provocar. Una estrategia ATM coloca el stop y el objetivo en el
  MISMO instante en que se llena la entrada, y en ese instante la posicion todavia se esta
  actualizando: las protecciones se calculaban contra una posicion a medio hacer.

  Ahora se provoca a voluntad, y se ha visto el hueco con los ojos: al calcular las
  protecciones, NinjaTrader decia que la posicion era de 1 dolar; al enviarlas, de 36. Una
  treintaiseisava parte. El arreglo que tapa eso --mirar la posicion dos veces, al calcular y
  al enviar-- estaba puesto desde la 0.4.2 y nunca se habia podido ejercer. Funciona: las dos
  protecciones llegaron a Hyperliquid del tamaño exacto de la posicion, las dos sin poder
  abrir nada, y atadas entre si como deben.

  Y encadenado con lo anterior: sacar un parcial justo despues de esa carrera deja las dos
  protecciones en el tamaño de lo que queda, en Hyperliquid y en el grafico. Las dos cosas
  que mas se piden juntas, probadas juntas.

  Estas dos comprobaciones se han añadido al recorrido completo, asi que se repiten en cada
  version a partir de ahora.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

