# Riesgo Vial Mapa

Mapa interactivo que pinta carreteras por riesgo historico + condiciones actuales de trafico y clima. Consume el backend local en `http://localhost:8080/api/tiempo-real`.

## Levantar localmente

1. Primero levanta el backend Docker desde el repo `riesgo-vial-backend`:

```powershell
docker compose up --build
```

2. En otra terminal entra al repo del mapa:

```powershell
cd .\riesgo-vial-mapa
```

3. Sirve los archivos estaticos en el puerto `5500`.

Si tienes Python instalado:

```powershell
python -m http.server 5500
```

Si PowerShell no encuentra Python, usa Node:

```powershell
npx.cmd serve . -l 5500
```

4. Abre el mapa:

```text
http://localhost:5500
```

## Datos requeridos

```text
data/carreteras_peru.geojson
data/riesgo_base_carreteras.json
data/modelo_export.json
```

El mapa espera que el backend responda en:

```text
http://localhost:8080/api/tiempo-real
```

## Actualizacion por zonas

El backend devuelve zonas de tiempo real para evitar una consulta por cada carretera. El mapa asigna cada carretera a la zona cercana, combina:

```text
35% historico + 65% actual
```

y nunca deja que una condicion actual alta quede por debajo del riesgo actual calculado.
