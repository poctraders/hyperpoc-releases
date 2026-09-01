# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.3.1.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.3.1 - Manual.pdf` | El manual completo, 68 páginas con capturas. |
| `hyperpoc 0.3.1.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
BEE094222D75090338BE683355DDEAAC41A25E38A045B8A4813B4D04AA98E805
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.3.1.exe" SHA256
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
2. Doble clic en `hyperpoc 0.3.1.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.3.1

```
0.3.1 Beta  (02/09/2026)
  CATORCE DIAS DE PRUEBA, Y DESPUES LICENCIA. Esta es la primera version que pide licencia
  para operar. La prueba no hay que activarla ni pedirla: empieza sola la primera vez que
  abres el programa y dura catorce dias completos, sin registrarse, sin dar un correo y sin
  ninguna limitacion mientras dura.

  CUANDO SE ACABA, LO UNICO QUE DEJA DE PODERSE ES ABRIR POSICION NUEVA. Cerrar, reducir y
  cancelar siguen funcionando siempre, pase lo que pase con la licencia: un stop, un
  objetivo, una cancelacion y el boton Close salen igual con la prueba agotada que el primer
  dia. Dejar a alguien encerrado dentro de una posicion con dinero real para cobrarle una
  licencia no es una forma aceptable de cobrar. Se cobra impidiendo entrar, nunca impidiendo
  salir.

  Y SI ALGO NO SE PUEDE COMPROBAR, SE DEJA OPERAR. Si el fichero no se deja leer, si el
  registro de Windows esta restringido por una directiva, o si falla cualquier otra cosa de
  nuestro lado, el programa NO concluye que no tienes licencia: te deja seguir. Un fallo
  nuestro no puede convertirse en un cliente que se queda sin poder operar.

  ACTIVAR LA LICENCIA ES PEGARLA, NO BUSCAR UNA CARPETA. En la ventana de conexion hay un
  boton nuevo, "Activar licencia...". Se abre, se pega entero el bloque que te mandamos, se
  pulsa Activar y ya esta: no tienes que encontrar ninguna carpeta ni copiar ningun fichero
  a mano. Se comprueba ANTES de guardar nada, asi que un bloque mal pegado te lo dice en el
  momento en vez de dejarte peor de lo que estabas.

  EL ID DE INSTALACION, CON SU BOTON DE COPIAR, en esa misma ventana y tambien en "Acerca
  de". Es lo unico que tienes que mandarnos para que te emitamos la licencia.

  UNA LICENCIA, DOS ORDENADORES. Se emite para dos IDs de instalacion -- el de sobremesa y
  el portatil, por ejemplo -- y el mismo bloque sirve en los dos.

  EL CONTADOR DE LA PRUEBA, EN "ACERCA DE", en dias y horas. El ultimo dia es justo el que
  importa: "queda 1 dia" pueden ser veintitres horas o veinte minutos, y no se decide lo
  mismo. Cuando ya hay licencia, ese mismo renglon dice a nombre de quien esta.

  Y SE AVISA UNA VEZ AL CONECTAR, solo cuando la prueba acaba de empezar o cuando ya se ha
  agotado. Una vez por sesion, y nunca si tienes licencia.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

