# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 1.2.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 1.2 - Manual.pdf` | El manual completo, 40 páginas con capturas. |
| `hyperpoc 1.2.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
25C2B024AD3B36B73EAC66FDC26F5BF57D951AD08108141791D1C56C55F4ECB0
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 1.2.exe" SHA256
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
2. Doble clic en `hyperpoc 1.2.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 1.2

```
1.2  (01/08/2026)
  ES LA MISMA APLICACION QUE LA 1.1, y conviene decirlo claro: mismo motor, mismos
  complementos, mismo comportamiento. No hay ningun arreglo nuevo que buscar.

  QUE CAMBIA ENTONCES: el paquete entero -- instalador, manual y este fichero -- se ha
  construido de una sola vez y lleva UN solo numero y UN solo hash. En la 1.1 el manual
  se amplio despues de haber construido el instalador, y aunque el .exe no cambio ni un
  byte, quedaban dos contenidos distintos bajo el mismo numero. Eso es exactamente lo
  que hace que un dia el hash que anuncia el README no sea el del archivo que tienes al
  lado, y que quien lo comprueba concluya que el archivo viene manipulado.

  SI VIENES DE LA 1.1: no tienes que hacer nada. Si aun asi la instalas, se instala
  encima sin tocar tu configuracion ni tu clave.

  SI VIENES DE LA 1.0 O DE UNA 0.x: aqui esta todo lo que trajo la 1.1 -- el aviso al
  reconectar ya no dice que tu cuenta "siguio operando sola" (afirmaba una causa que el
  programa no puede conocer), se te dice en cada conexion cuantas API wallets pueden
  firmar en tu cuenta, y hay un "Acerca de" al final del menu con la version, el
  contacto y el copyright. El manual explica ademas de donde se bajan las versiones
  nuevas y como mirar la que tienes.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

