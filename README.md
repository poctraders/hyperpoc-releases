# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.2.7.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.2.7 - Manual.pdf` | El manual completo, 0 páginas con capturas. |
| `hyperpoc 0.2.7.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
881A275965536FDE2E98F7DF5A6ABD30BA5A352788DA1F299167ADDAF4069EB8
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.2.7.exe" SHA256
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
2. Doble clic en `hyperpoc 0.2.7.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.2.7

```
0.2.7 Beta  (18/08/2026)
  LA VENTANA DE "HAY UNA VERSION NUEVA", CON TRES BOTONES QUE HACEN LO QUE DICEN.

  DESCARGAR ya no te deja en la pagina buscando el fichero: le da a tu navegador el enlace
  del instalador y la descarga empieza sola. Antes de pulsar, la ventana te dice QUE fichero
  va a bajar y CUANTO PESA. Sigue sin bajarlo ni ejecutarlo este programa: lo guarda tu
  navegador, con su aviso de descarga, y lo abres tu. Y NinjaTrader se cierra, como siempre,
  porque el instalador no puede sustituir ficheros que estan en uso.

  RECORDARMELO MAS TARDE ahora son TRES DIAS de verdad. Antes no anotaba nada, asi que si
  abrias y cerrabas NinjaTrader tres veces en una manana veias el mismo cartel tres veces --
  la mejor forma de acabar cerrandolo sin leerlo. Si mientras tanto sale una version
  POSTERIOR, se te avisa igual: aplazar una no tapa la siguiente.

  CANCELAR calla el aviso hasta que vuelvas a abrir NinjaTrader. No anota nada en ningun
  sitio. Cerrar la ventana con la X hace lo mismo.

  Se va el boton de "descartar esta version", que anotaba en disco una version y no volvia a
  mencionarla nunca. Si no quieres saber nada de las actualizaciones, la casilla de "Acerca
  de" lo apaga entero -- y esa se ve y se puede volver a encender.

  Y el enlace verde de la ventana lleva a la pagina de la version, que es donde estan las
  notas y el SHA256 si quieres comprobarlo. Ese no cierra NinjaTrader ni la ventana.

  UN SOLO ICONO DE NINJATRADER EN EL ESCRITORIO. El icono que instala este programa abre
  NinjaTrader haciendo antes la revision que deja su base de datos coherente con Hyperliquid.
  La idea era que sustituyera al de NinjaTrader; en realidad se quedaban los dos, uno al lado
  del otro, y la mitad de las veces se pulsaba el que se salta esa revision. Ahora el viejo se
  quita al instalar. Si desinstalas hyperpoc, se te devuelve: no vas a quedarte sin forma de
  abrir NinjaTrader por haber quitado esto.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

