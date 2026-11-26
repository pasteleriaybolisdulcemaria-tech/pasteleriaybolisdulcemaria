# Dulce María — Pastelería y Bolis Gourmet

Sitio estático (HTML/CSS/JS) listo para GitHub + Vercel. Incluye carrito solo para **Bolis** y **Recetario PDF**, pago con **Wompi** y catálogo sin precios para tortas y repostería.

## 1. Imágenes
Todo va incrustado en `index.html` (fotos, logo, mascota y fondo): no necesitas subir ninguna carpeta de imágenes.

## 2. Configurar
Edita `index.html` (bloque «CONFIGURACIÓN», al final del archivo): llave pública de Wompi y enlace de cotización. El enlace del PDF NO va en el código: se guarda en Vercel como variable `RECETARIO_PDF_URL` (ver Wompi, paso 2). En `index.html` busca los comentarios `CONFIRMAR` y verifica cuál Facebook es de cada línea.

## 3. Wompi
1. En el panel de Wompi (Desarrolladores) copia tu **Llave pública** → `WOMPI_PUBLIC_KEY`.
2. En Vercel agrega también `RECETARIO_PDF_URL` con el enlace de tu PDF (en Drive: *Compartir → Cualquier persona con el enlace*). Solo se entrega tras un pago aprobado.
2b. Copia tu **Secreto de integridad** → en Vercel: *Settings → Environment Variables* → `WOMPI_INTEGRITY_SECRET` (nunca lo pongas en el código).
3. En Wompi registra la URL de eventos/redirección si te la piden: `https://TU-DOMINIO.vercel.app/gracias.html`.
4. Prueba primero con llaves `pub_test_…` y cambia `WOMPI_API` a `https://sandbox.wompi.co/v1`.

Alternativa sin llaves: crea un enlace de pago en Wompi y pégalo en `WOMPI_PAYMENT_LINK` (monto fijo, sirve p. ej. solo para el recetario).

> Nota: la entrega del PDF verifica el pago en el navegador. Para mayor seguridad, usa un enlace de descarga que no compartas en otro lado (p. ej. Drive con enlace privado) o más adelante genera enlaces firmados con un webhook.

## 4. GitHub
```bash
cd dulce-maria
git init
git add .
git commit -m "Sitio Dulce María"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/dulce-maria.git
git push -u origin main
```
(Crea antes el repositorio vacío en github.com → *New repository*.)

## 5. Vercel
1. Entra a vercel.com → *Add New… → Project* → importa el repo.
2. *Framework Preset*: **Other**. No cambies build ni output.
3. Agrega la variable `WOMPI_INTEGRITY_SECRET` y pulsa **Deploy**.
4. Cada `git push` republica automáticamente. Dominio propio: *Settings → Domains*.

## Si la página se ve sin diseño o sin fotos
- Descomprime el ZIP primero (no lo abras desde dentro del ZIP).
- Sube a GitHub el **contenido** de la carpeta `dulce-maria` (que `index.html` y la carpeta `api` queden en la raíz del repositorio, no dentro de otra carpeta).
