# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.1.1.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.1.1 - Manual.pdf` | El manual completo, 51 páginas con capturas. |
| `hyperpoc 0.1.1.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
B255C857750F03B355841C2475685FE72727BA4D97DF601ACDBB5D79CBD47230
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.1.1.exe" SHA256
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
2. Doble clic en `hyperpoc 0.1.1.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.1.1

```
0.1.1 Beta  (11/08/2026)
  NUMERACION NUEVA. A partir de aqui las versiones van como 0.x.x Beta: la primera cifra
  sube con los cambios grandes y la segunda con los menores. Mientras ponga 0.x.x, esto es
  una beta y se dice claro. Esta version trae, ademas, todo lo que sigue.

  AL PULSAR EL ICONO DE NINJATRADER, TODO SE PONE EN ORDEN SOLO. Esta version trae una
  revision que deja la base de datos de NinjaTrader coherente con Hyperliquid antes de
  abrirlo: cuenta plana --para que tu posicion REAL se repinte desde Hyperliquid en vez de
  arrastrar lo que el simulador creyera-- sin fichas de instrumento duplicadas y sin
  referencias colgadas de las que impiden que NinjaTrader llegue a arrancar.

  ESA REVISION NO SE ESTABA EJECUTANDO EN TU ORDENADOR. Existia desde hace tiempo, pero solo
  la lanzaba una herramienta interna que NO se distribuye: despues de instalar, no corria
  NUNCA. Ahora el icono de NinjaTrader del Escritorio la ejecuta y abre NinjaTrader a
  continuacion, sin ventanas, sin preguntas y sin que tengas que saber que existe. Si por lo
  que sea no pudiera hacerse, NinjaTrader se abre igual: quedarte sin plataforma por una
  limpieza seria peor que el problema que evita.


  LO QUE PONGAS FUERA DE NINJATRADER YA APARECE EN NINJATRADER. Si dejabas una orden desde
  la web de Hyperliquid, o desde otro ordenador, NinjaTrader NO la enseñaba. Lo detectaba
  --lo escribia en el registro-- pero se limitaba a decir "reconecta para que NT las
  refleje". O sea: ordenes vivas, con tu dinero, que tu pantalla no mostraba, y para verlas
  tenias que leer un fichero de registro y reconectar a mano.

  Ahora NinjaTrader se pone al dia solo, con la misma maquinaria del "Conectar". Espera dos
  vueltas antes de hacerlo --entre que Hyperliquid acepta una orden y NinjaTrader la refleja
  hay unos segundos que son normales-- y lo intenta UNA vez por cada juego de ordenes: si
  aun asi no se reflejan (por ejemplo un instrumento que no tienes dado de alta), lo dice y
  no insiste, en vez de quedarse reiniciandose en bucle.

  Con esto, las dos plataformas se persiguen en los dos sentidos: lo que NinjaTrader tiene y
  Hyperliquid no, se limpia; lo que Hyperliquid tiene y NinjaTrader no, se refleja.

  Y DEJA DE ACUMULAR COPIAS DE SEGURIDAD. La revision que corre al abrir NinjaTrader hacia
  una copia de la base de datos (4,8 MB) CADA VEZ, y no borraba ninguna: se habian juntado
  12 copias, 76 MB. Quien abre NinjaTrader a diario se comia mas de un giga al año en
  copias que no mira nadie. Ahora se guardan las 3 ultimas.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

