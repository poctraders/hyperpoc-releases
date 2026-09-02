# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.3.2.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.3.2 - Manual.pdf` | El manual completo, 68 páginas con capturas. |
| `hyperpoc 0.3.2.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
5ABCC9DD15285ED8654239FD2C326F0B1CB2580C4B5FB7D805516A294E1DFB96
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.3.2.exe" SHA256
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
2. Doble clic en `hyperpoc 0.3.2.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.3.2

```
0.3.2 Beta  (02/09/2026)
  LA CLAVE DE ADMINISTRADOR, UNA VEZ METIDA, SE QUEDA EN EL ORDENADOR. Hasta ahora toda la
  activacion colgaba de un unico fichero: bastaba borrar la carpeta de datos, reinstalar
  desde cero o pegar cualquier otra cosa encima para quedarse fuera y tener que volver a
  pedir la clave. "Activado" no puede significar "mientras ese fichero siga ahi". Ahora,
  al aceptarla, queda anotado en el propio ordenador, y ese equipo sigue activado aunque el
  fichero desaparezca, aunque se desinstale y se vuelva a instalar, y sin fecha de
  caducidad.

  NO DEPENDE DEL ID DE INSTALACION, ni para meterla ni para conservarla. Funciona igual en
  un equipo donde ese ID ni siquiera se puede calcular -- los hay, con el registro de
  Windows restringido por directiva --, que era justo donde antes fallaba.

  Y UNA LICENCIA COMPRADA MANDA POR ENCIMA. Si en ese mismo ordenador se activa despues una
  licencia de verdad, "Acerca de" pasa a enseñar el nombre de su titular. Lo que se ha
  pagado no se queda tapado detras de una clave de pruebas.

  La anotacion va sellada y no lleva la clave dentro: escribirla a mano no activa nada, y
  quien mire ahi no saca de ella ninguna clave. El informe de soporte dice ahora si el
  ordenador esta en ese estado, para no salir a buscar un problema de licencia que no
  existe.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

