# Variables de la firma

La plantilla `firma_gmail.html` conserva estas variables:

```text
{NOMBRE}
{CARGO}
{EMPRESA}
{TELEFONO}
{WHATSAPP_LINK}
{CORREO}
{DIRECCION}
{WAZE_URL}
{SLOGAN}
```

En el generador, el usuario solo edita:

```text
NOMBRE
CARGO
TELEFONO
CORREO
```

Los datos corporativos permanecen fijos:

```text
EMPRESA = Corporación Carrousel, S.A.
DIRECCION = 15 Calle A 7-53, Zona 9, Guatemala
SLOGAN = ¡Somos alegría!
```

## Normalización automática

Antes de copiar o descargar la firma, el generador:

- elimina espacios sobrantes y caracteres invisibles;
- convierte el nombre a mayúsculas;
- aplica capitalización uniforme al cargo y conserva siglas comunes;
- convierte teléfonos locales o con prefijo `502` al formato `0000-0000`;
- convierte el correo a minúsculas y elimina espacios internos;
- usa el número completo con código `502` para el enlace de WhatsApp.

Valores usados para la prueba:

```text
NOMBRE = ROCÍO CASTRO
CARGO = Gerente de Gestión Humana
EMPRESA = Corporación Carrousel, S.A.
TELEFONO = 3001-1955
WHATSAPP_LINK = https://wa.me/50230011955
CORREO = rocio.castro@carrousel.com.gt
DIRECCION = 15 Calle A 7-53, Zona 9, Guatemala
WAZE_URL = enlace corporativo de Waze
SLOGAN = ¡Somos alegría!
```

## Fuentes

El PDF exportado incrusta estas fuentes:

- `VAGRoundedNextShine-Regular`: nombre y cargo, convertido en el PDF como fuente Type3.
- `Montserrat-Regular`: empresa, teléfono, correo, dirección y slogan.

En Gmail no se deben incrustar fuentes. Por eso `firma_gmail.html` usa la pila:

```css
Nombre/cargo: 'VAGRoundedNextShine-Regular', 'Arial Rounded MT Bold', Arial, Helvetica, sans-serif
Resto: Montserrat, Arial, Helvetica, sans-serif
```

Si el equipo que ve la firma no tiene `VAGRoundedNextShine-Regular` o `Montserrat`, Gmail usará las fuentes de respaldo. `Arial Rounded MT Bold` es el fallback más cercano disponible localmente para el bloque del nombre/cargo.

## Diferencias inevitables

- Gmail no respeta siempre fuentes web ni CSS avanzado, por lo que la firma final usa tablas, estilos inline y fuentes seguras.
- El logo obligatorio de Drive sustituye al logo incrustado en Canva y tiene un fondo oscuro propio. Se mantiene la zona visual del logo del diseño maestro y se escala sin deformación.
- Las líneas de color se reconstruyen con celdas de tabla en vez de usar el recorte auxiliar `width_1600`, para no depender de archivos locales ni convertir la firma en una imagen.
- La estrella inferior se reconstruyó como carácter tipográfico amarillo para evitar el recorte/padding del PNG público y acercarla al aspecto simple que se ve en el PDF.
