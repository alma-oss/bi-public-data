# How to use Administrative units
The folder contains GeoJson files for administrative units in:
* Czech Republic
* Poland
* Slovakia

Every Geojson has reference via NUTS or TERYT code for Polish powiats to the tables described below in Snowflake MANUAL_INPUT schema

## Czech Republic and Slovakia
We use NUTS3 (Kraje) and NUTS4/LAU1 (Okresy). NUTS2 are not widely used in Czech Republic - it is called "Regiony soudržnosti"

#### Okresy

Data structure:
```yaml
  - name: cz_nuts4_lau1_okresy
    columns:
    - name: nuts_code
      data_type: text
    - name: iso_code
      data_type: text
    - name: csu_code
      data_type: text
    - name: cuzk_code
      data_type: number
    - name: nuts3_code  <-- This is reference to Kraje (NUTS_CODE)
      data_type: text
    - name: name
      data_type: text

```

#### Kraje

Data structure:
```yaml
  - name: cz_nuts3_kraje
    columns:
    - name: nuts_code
      data_type: text
    - name: iso_code
      data_type: text
    - name: csu_code
      data_type: text
    - name: cuzk_code
      data_type: number
    - name: name
      data_type: text
```
___
## Poland
We use NUTS2 (Wojewodztwo) and NUTS4/LAU1 (Powiaty), unfortunately Poland has system called TERYT for identifying LAU1 units that's why data contain TERYT codes as well.

#### Powiaty

Data structure:
```yaml
  - name: pl_nuts4_lau1_powiaty
    columns:
    - name: name
      data_type: text
    - name: teryt_code
      data_type: text
    - name: nuts2_code <-- This is reference to Wojewodztwo (NUTS_CODE)
      data_type: text

```

#### Wojewodztwo

Data structure:
```yaml
  - name: pl_nuts2_wojewodztwo
    columns:
    - name: nuts_code
      data_type: text
    - name: iso_code
      data_type: text
    - name: teryt_code
      data_type: text
    - name: name
      data_type: text
```