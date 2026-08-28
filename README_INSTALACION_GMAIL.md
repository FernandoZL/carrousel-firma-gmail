# Instalación en Gmail

1. Abre `generador_firmas.html` en el navegador.
2. Cambia los datos del empleado en el formulario.
3. Pulsa `Copiar firma para Gmail`.
4. En Gmail, abre `Configuración` > `Ver toda la configuración` > `Firma`.
5. Crea una firma nueva o edita una existente y pega el contenido copiado.
6. Guarda los cambios al final de la página de configuración.

También puedes abrir `firma_gmail.html`, seleccionar la tabla de la firma y copiarla, pero el generador evita editar HTML a mano.

## Recursos remotos

La firma usa imágenes remotas HTTPS para que el destinatario pueda verlas:

- Logo autorizado de Google Drive: `https://drive.google.com/thumbnail?id=10wDyr5nlIfqjMmOociguZfsWFHeGnTuq&sz=w1600`
- Icono teléfono de Canva: `https://media-public.canva.com/DJJ5c/MAFkYODJJ5c/1/t.png`
- Icono correo de Canva: `https://media-public.canva.com/NDCS0/MAGOMKNDCS0/1/t.png`
- Icono ubicación de Canva: `https://media-public.canva.com/1stEg/MAGL8H1stEg/1/t.png`

El enlace del logo fue probado con respuesta HTTP `200`, tipo `image/png`.
