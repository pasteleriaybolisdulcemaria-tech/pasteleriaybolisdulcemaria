# Dulce María — Pastelería y Bolis Gourmet

Sitio estático (HTML/CSS/JS) listo para GitHub + Vercel. Incluye carrito solo para **Bolis** y **Recetario PDF**, pago con **Wompi** y catálogo sin precios para tortas y repostería.

## 1. Imágenes (ya incluidas)
```
assets/img/logo.jpg · mascota.jpg · favicon.png (el logo, la mascota y el fondo ya van incrustados en `index.html`)
assets/img/donas.jpg · bolis.jpg
assets/img/tortas/torta-1.jpg … torta-10.jpg
assets/img/cupcakes.jpg · flan.jpg · bolis-1.jpg … bolis-5.jpg
```
Las fotos de tortas ya están recortadas por abajo para ocultar el número de WhatsApp. Si agregas más, recórtalas igual antes de subirlas y añade su número en la lista `[1,2,3,4,5,6,7,8,9,10]` de `assets/js/app.js`.

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
- En GitHub, sube el **contenido** de la carpeta `dulce-maria` (que `index.html` quede en la raíz del repositorio, no dentro de otra carpeta) y que exista la carpeta `assets/img/` con sus fotos.
- Las fotos de tortas, bolis y repostería se leen de `assets/img/`; el diseño, logo y mascota funcionan aunque solo subas `index.html`.
