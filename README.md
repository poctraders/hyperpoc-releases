# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.2.2.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.2.2 - Manual.pdf` | El manual completo, 65 páginas con capturas. |
| `hyperpoc 0.2.2.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
142F2110B4A74417787049A643213D0A841B85C49A943F1448932A77FB7E0DEA
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.2.2.exe" SHA256
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
2. Doble clic en `hyperpoc 0.2.2.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.2.2

```
0.2.2 Beta  (15/08/2026)
  UN BOTON PARA CUANDO ALGO NO VA. En el menu Inicio, dentro de "Hyperliquid para NinjaTrader 8",
  hay una entrada nueva: "Informe para soporte". Deja en el Escritorio un unico fichero .zip con
  todo lo que hace falta para averiguar que esta pasando -- que version tienes, donde esta cada
  pieza, si el adapter esta bien puesto dentro de NinjaTrader, como esta tu configuracion y los
  registros de las ultimas sesiones.

  Hasta ahora, pedir ayuda era que te dictaramos rutas por correo: abre esta carpeta, busca ese
  fichero, dime que pone. Cada vuelta era un dia. Ahora se adjunta el zip y ya esta.

  TU CLAVE NO VA DENTRO, y no es una promesa: de la configuracion solo se copian los campos que
  estan nombrados uno a uno, y cualquier otro sale sustituido por su longitud. Ademas se tacha
  del contenido de los registros cualquier cosa con forma de clave privada o de contrasena,
  aunque sea de hace semanas y ya no se use. Tu direccion publica si va: es publica de por si y
  sin ella no se puede mirar nada.

  Funciona con NinjaTrader CERRADO, que es justo cuando uno quiere mirar, y no se conecta a
  Hyperliquid para hacerlo.

  Y SI TIENES UN PROBLEMA, AHORA WINDOWS TE MANDA A DONDE HAY QUE IR. En "Aplicaciones
  instaladas", este programa daba como pagina de soporte la de Hyperliquid, que no sabe nada de
  el y no te puede ayudar.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

