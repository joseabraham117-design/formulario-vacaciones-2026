# Formulario web — Vacaciones octubre 2026

## Incluye
- Formulario público optimizado para celular.
- Campo obligatorio APELLIDOS Y NOMBRES.
- Si marca NO, puede enviar directamente.
- Si marca SÍ, aparecen fechas de inicio y fin, limitadas a octubre de 2026.
- Base de datos SQLite (`vacaciones.db`).
- Panel privado `/admin`, conteos y exportación Excel `.xlsx`.

## Ejecutar en Windows
1. Instale Python 3.11 o posterior.
2. Abra PowerShell dentro de esta carpeta.
3. Ejecute:
   ```powershell
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   pip install -r requirements.txt
   $env:ADMIN_PASSWORD="use-una-clave-larga-y-unica"
   $env:SECRET_KEY="use-una-clave-secreta-aleatoria"
   py app.py
   ```
4. Formulario: `http://127.0.0.1:5000`
5. Panel: `http://127.0.0.1:5000/admin`

Configure `ADMIN_PASSWORD` y `SECRET_KEY` antes de usarlo. La aplicación no permitirá iniciar sesión con la contraseña predeterminada.

## Para hacerlo público
Debe publicarse en un servidor compatible con Flask. Netlify por sí solo no aloja esta aplicación Flask tradicional. La base de datos debe estar en almacenamiento persistente; para plataformas sin disco persistente, conviene usar PostgreSQL administrado y adaptar la aplicación.

## Limitaciones de esta primera versión
- No permite editar respuestas desde el panel.
- No evita duplicados: como el formulario público solo solicita el nombre, dos envíos de la misma persona pueden guardarse.
- Cada exportación Excel es una instantánea; vuelva a exportar para incluir respuestas nuevas.
