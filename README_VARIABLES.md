# Variables de la firma

La plantilla `firma_gmail.html` conserva estas variables:

```text
{NOMBRE}
{CARGO}
{EMPRESA}
{TELEFONO}
{TELEFONO_LINK}
{CORREO}
{DIRECCION}
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

Valores usados para la prueba:

```text
NOMBRE = ROCÍO CASTRO
CARGO = Gerente de Gestión Humana
EMPRESA = Corporación Carrousel, S.A.
TELEFONO = 3001-1955
TELEFONO_LINK = 30011955
CORREO = rocio.castro@carrousel.com.gt
DIRECCION = 15 Calle A 7-53, Zona 9, Guatemala
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
