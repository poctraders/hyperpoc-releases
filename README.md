# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 1.4.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 1.4 - Manual.pdf` | El manual completo, 51 páginas con capturas. |
| `hyperpoc 1.4.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
22D84D8A88973773EF7E525251BD670526E001080E50A7987B852F8F4DD001D6
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 1.4.exe" SHA256
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
2. Doble clic en `hyperpoc 1.4.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 1.4

```
1.4  (04/08/2026)
  EL CODIGO VA BLINDADO. Los tres ensamblados .NET (el addon, el adapter y el registro de la
  conexion) y el motor Python se reparten ahora OFUSCADOS: quien abra el instalador con un
  decompilador (dnSpy, ILSpy) ya no se encuentra el codigo en claro, sino nombres sin
  sentido, cadenas cifradas y flujo enrevesado. El motor Python deja de ser bytecode que se
  desempaqueta y se lee: ahora es codigo maquina de verdad (compilado con Nuitka).

  QUE CAMBIA PARA TI: NADA. Se conecta, opera y avisa exactamente igual; es el MISMO
  programa, solo que cuesta muchisimo mas robarlo y reutilizarlo. Ninguna clave viajaba ni
  viaja en los binarios (la tuya sigue cifrada con tu usuario de Windows), asi que esto no
  protege un secreto: protege el trabajo.

  LO HONESTO: ninguna proteccion de cliente es inviolable -- lo que hace es volver el robo
  caro y doloroso, y frenar en seco la copia casual. Es ademas el cimiento del sistema de
  claves de instalacion que viene despues: sin este blindaje, cualquier control de licencia
  se quitaria en cinco minutos con un decompilador.

  EFECTO SECUNDARIO: al ir SIN FIRMA y con la proteccion al maximo, SmartScreen o algun
  antivirus pueden quejarse mas de la cuenta la primera vez ("Mas informacion" -> "Ejecutar
  de todas formas"). Es el precio de blindarlo fuerte sin un certificado de firma.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

