# hyperpoc — Hyperliquid para NinjaTrader 8

Opera tu cuenta de **Hyperliquid** desde los gráficos de **NinjaTrader 8**: sus mercados en el
buscador de instrumentos, sus velas en los gráficos y tus órdenes reales desde el Chart Trader.

**Descargar la última versión → [Releases](https://github.com/poctraders/hyperpoc-releases/releases/latest)**

Esta página es solo de descargas. El código fuente no está aquí: es privado.

---

## Qué te llevas

| Archivo | Qué es |
|---|---|
| `hyperpoc 0.2.4.exe` | El instalador. Sirve para **instalar, reparar y desinstalar**. Es lo único que hay que ejecutar. |
| `hyperpoc 0.2.4 - Manual.pdf` | El manual completo, 65 páginas con capturas. |
| `hyperpoc 0.2.4.zip` | Los dos anteriores juntos, más un README con las instrucciones. |

**SHA256 del instalador**

```
A71C8B56C991D4F180F4641F80D1879EF7FA08AB1CBE46982008EDAB1748163A
```

Compruébalo antes de ejecutarlo, en una ventana de comandos y en la carpeta donde lo hayas
dejado:

```
certutil -hashfile "hyperpoc 0.2.4.exe" SHA256
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
2. Doble clic en `hyperpoc 0.2.4.exe`. Windows mostrará una pantalla azul porque el archivo no
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

## Novedades de la 0.2.4

```
0.2.4 Beta  (17/08/2026)
  EL GRAFICO SE VE IGUAL DE BIEN EN UN MONITOR 4K. Lo que este programa pinta encima del
  grafico se dibujaba con un tamano fijo en pixeles, mientras que las letras del propio
  NinjaTrader crecen solas cuando Windows escala la pantalla. En un 4K el resultado era que
  nuestro texto salia MAS PEQUENO que el de al lado, y costaba leerlo justo cuando mas
  falta hace. Ahora todo -- la letra, los margenes y el grosor de la linea -- crece en la
  misma proporcion que el resto del grafico. En un monitor normal no cambia nada.

  Y NO ES "SUBIR LA FUENTE", que ya se probo en su dia y salio mal: a mayor tamano el
  cartel se comia el grafico en las pantallas normales. Es que se vea IGUAL DE GRANDE en
  todas, que es otra cosa.

  LA LEYENDA DE LA LIQUIDACION, SIEMPRE ABAJO. Antes colgaba de la linea: subia y bajaba con
  el precio, tapaba las velas por las que pasara y, con la liquidacion fuera de pantalla,
  saltaba al borde de arriba. Con una posicion abierta eso se mira de reojo, y un cartel que
  hay que localizar antes de leerlo no sirve de nada. Ahora esta siempre en el mismo sitio,
  en la parte baja, diciendo donde esta el punto de liquidacion. La linea sigue en su precio;
  lo que deja de moverse es el texto.

  Y EL APALANCAMIENTO SE VA DEL GRAFICO. El "x30 Cross - libre para abrir: ..." que salia en
  una esquina era el MISMO dato que ya tienes en el panel de ordenes, justo al lado de donde
  tecleas la cantidad, que es donde se mira antes de entrar. Encima del grafico solo tapaba
  velas. El grafico queda para lo que si es suyo: donde te liquidan.
```

---

© 2026 [Poctraders](https://www.poctraders.com) · [info@poctraders.com](mailto:info@poctraders.com)

NinjaTrader es una marca de NinjaTrader Group, LLC, ajena a Poctraders.

