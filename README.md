# Riesgo Vial Mapa

Mapa interactivo para GitHub Pages. Muestra carreteras como líneas tipo tráfico y actualiza datos en tiempo real desde el backend de Vercel.

## Estructura

```text
index.html
data/
  carreteras_peru.geojson
  riesgo_base_carreteras.json
  camaras_lima.json
```

## Archivos obligatorios

```text
data/carreteras_peru.geojson
data/riesgo_base_carreteras.json
```

`carreteras_peru.geojson` debe contener líneas reales de carreteras con un código compatible:

```text
COD_CARRETERA
RUTA
CODIGO
cod_carretera
ruta
codigo
```

`riesgo_base_carreteras.json` debe venir de Gold/Colab y tener `COD_CARRETERA`.

## Backend en tiempo real

El mapa consulta este endpoint:

```text
https://riesgo-vial-backend.vercel.app/api/tiempo-real
```

Si Vercel te da otra URL, cambia esta línea en `index.html`:

```js
backendTiempoReal: "https://riesgo-vial-backend.vercel.app/api/tiempo-real"
```

por tu URL real.

## Activar GitHub Pages

En GitHub:

```text
Settings → Pages → Deploy from a branch → main → root
```

## Importante

Los archivos de la carpeta `data/` son de ejemplo. Debes reemplazarlos por tus datos reales exportados desde Databricks/Gold y por un GeoJSON real de carreteras.
