# Kiosco App — inventario, ventas y fiados (APK)

App para un kiosco: productos con stock, ventas con varias líneas, cobro en $, € o Bs con vuelto, **Fiado** (el cliente se lleva el producto y paga después), cobranza por cliente, cierre del día con conteo y gráficos. Funciona sin internet; los datos viven dentro del teléfono.

## Pestañas
- **Inicio:** tasa de hoy, vendido hoy, total por cobrar, stock bajo, ingresos de 7 días y Ajustes (Compartir, Recibir).
- **Almacén:** solo productos (precio, costo, stock, mínimo). Comprar, Ajustar, Editar. Buscador por nombre.
- **Vender:** buscador, orden con varias líneas y cobro. Métodos: Pago móvil o Transferencia, Efectivo, Débito, Otro y **Fiado**.
- **Ventas:** ventas del día con detalle, método y moneda, fiados, abonos cobrados y Anular.
- **Por cobrar:** clientes con deuda: total, órdenes con fecha y productos detallados, Abonar/Pagar, cambiar nombre. Buscador por cliente.
- **Gráficos:** ventas, ganancia, gastos, más vendidos y métodos de pago (7/30/90 días) y **Cierre del día** (conteo de productos).

## Reglas
- Precios en **$**; el equivalente en Bs usa la **tasa de hoy** (obligatoria para cobrar en Bs/€).
- **Fiado:** exige nombre del cliente; se puede combinar con otros métodos (paga una parte, el resto queda debiendo; sin vuelto). El stock se descuenta al vender.
- **Abonos:** parciales o totales, en cualquier moneda y método; se aplican primero a las órdenes más viejas. Una venta con abonos no se puede anular.
- Una venta fiada cuenta como vendida el día que se hace; el dinero de un abono aparece en **Cobrado de deudas** el día que se recibe.
- Cada venta guarda precios, costo, tasa y cliente del momento.

## Compartir / Recibir
Inicio → Ajustes → **Compartir** genera un mensaje con código comprimido y verificado (`KIOSCO1|…`); en el otro teléfono: **Recibir** → pegar → Reemplazar (hay *Deshacer*). Incluye las deudas. No es sincronización: el receptor ve una foto del momento.

## App independiente
`appId` = `com.moussacorp.kiosco` y clave de datos `kiosco.v1`: no comparte instalación ni datos con la app de comida. **No cambies** el `appId` ni la clave de datos en futuras versiones.

## Compilar el APK en GitHub (sin instalar nada)
1. Repo **PRIVADO**. Copia tu `debug.keystore` junto a `package.json` (misma llave para futuras actualizaciones).
2. Sube el contenido de la carpeta (*Add file → Upload files*) → *Commit changes*. Verifica que exista `.github/workflows/build-apk.yml`.
3. **Actions** → espera 5 a 8 min → ejecución con ✅ → **Artifacts** → `kiosco-app-apk` → `app-debug.apk`.
4. Pásalo al teléfono, permite "origen desconocido" y, si aparece, *Play Protect → Instalar de todos modos*.

Actualizaciones futuras: reemplaza solo `www/index.html` y se recompila solo.
