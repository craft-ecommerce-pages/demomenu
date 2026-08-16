# CLAUDE.md — Las Hamburguesas del Gordo Paul

Menú digital para **Las Hamburguesas del Gordo Paul** (smash burgers artesanales, Quito, Ecuador).

## Tecnología

Mismo stack que pizza-planet: HTML/CSS/JS vanilla, sin build. `index.html` + `config.json` + `productos.json` + `app.js` + `style.css`.

## Fuente de verdad de los productos

**craft-crm** (nodo core, producción). Los productos viven en la DB por `business_id`.
`catalogsync` regenera `productos.json` + la clave `categories` de `config.json` desde la DB y hace push a este repo → Cloudflare Pages despliega.

Todo lo demás de `config.json` (tema, tipografías, WhatsApp, ubicación, redes) lo controla este repo y **se preserva** en cada sync. No editar `productos.json` a mano.

## Datos del cliente

- **WhatsApp pedidos**: +593986131942
- **Ubicación**: Quito, Ecuador (mapa embebido en `config.location.map_embed`)
- **Cloudflare Pages**: `las-hamburguesas-del-gordo-paul.pages.dev`

## Branding

- **Paleta**: primary `#E4801C` (naranja) · accent `#F5B301` (ámbar) · fondo casi negro. En `config.json` (`theme_primary`/`theme_accent`) y defaults en `style.css`.
- **Tipografías**: Anton (títulos display) + DM Sans (cuerpo).

## Modelo de productos (hamburguesas)

- Variante **Presentación**: Simple / Doble / Triple (recargo por tamaño).
- Variante **Tipo**: Sola / Combo (+ papas fritas + cola).
- Variante **Vegetales** (solo las que llevan vegetales frescos): Con vegetales (lechuga, tomate, cebolla) / Sin vegetales.
- Imágenes: se cargan desde la UI de craft-crm (no viven en el repo).

## Deploy

```bash
git add . && git commit -m "descripción" && git push
```

Cloudflare Pages despliega automáticamente en push a `main` (workflow en `.github/workflows/deploy.yml`).
