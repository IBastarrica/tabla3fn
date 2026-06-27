# Normalización 1FN → 3FN

## Tabla original (desnormalizada)

| Título | Año | Duración | Tipo | Estudio | Dirección Estudio | Actor |
|---|---|---|---|---|---|---|
| Star Wars | 1977 | 124 | Color | Fox | Hollywood | Carrie Fisher |
| Star Wars | 1977 | 124 | Color | Fox | Hollywood | Mark Hamill |
| Star Wars | 1977 | 124 | Color | Fox | Hollywood | Harrison Ford |
| Mighty Ducks | 1991 | 104 | Color | Disney | Buena Vista | Emilio Estevez |
| Ben Hur | 1959 | 212 | Color | MGM | Hollywood | Charlton Heston |
| Ben Hur | 1959 | 212 | Color | MGM | Hollywood | Martha Scott |
| El retorno del Jedi | 1983 | 124 | Color | Fox | Hollywood | Carrie Fisher |

## 1FN → 2FN (eliminar dependencias parciales)

**Tabla: Peliculas**

| Título | Año | Duración | Tipo | Estudio | Dirección |
|---|---|---|---|---|---|
| Star Wars | 1977 | 124 | Color | Fox | Hollywood |
| Mighty Ducks | 1991 | 104 | Color | Disney | Buena Vista |
| Ben Hur | 1959 | 212 | Color | MGM | Hollywood |
| El retorno del Jedi | 1983 | 124 | Color | Fox | Hollywood |

**Tabla: Peliculas_Actores**

| Título | Actor |
|---|---|
| Star Wars | Carrie Fisher |
| Star Wars | Mark Hamill |
| Star Wars | Harrison Ford |
| Mighty Ducks | Emilio Estevez |
| Ben Hur | Charlton Heston |
| Ben Hur | Martha Scott |
| El retorno del Jedi | Carrie Fisher |

## 2FN → 3FN (eliminar dependencias transitivas)

**Tabla: Estudios**

| id_estudio | nombre | direccion |
|---|---|---|
| 1 | Fox | Hollywood |
| 2 | Disney | Buena Vista |
| 3 | MGM | Hollywood |

**Tabla: Peliculas**

| id_pelicula | titulo | año | duracion | tipo | id_estudio |
|---|---|---|---|---|---|
| 1 | Star Wars | 1977 | 124 | Color | 1 |
| 2 | Mighty Ducks | 1991 | 104 | Color | 2 |
| 3 | Ben Hur | 1959 | 212 | Color | 3 |
| 4 | El retorno del Jedi | 1983 | 124 | Color | 1 |

**Tabla: Actores**

| id_actor | nombre |
|---|---|
| 1 | Carrie Fisher |
| 2 | Mark Hamill |
| 3 | Harrison Ford |
| 4 | Emilio Estevez |
| 5 | Charlton Heston |
| 6 | Martha Scott |

**Tabla: Peliculas_Actores**

| id_pelicula | id_actor |
|---|---|
| 1 | 1 |
| 1 | 2 |
| 1 | 3 |
| 2 | 4 |
| 3 | 5 |
| 3 | 6 |
| 4 | 1 |

## Diagrama de relaciones

```
Estudios ──1:N──> Peliculas ──N:M──> Actores
                        │
                        └── Peliculas_Actores (tabla intermedia)
```

## Resumen

| Forma Normal | Acción realizada |
|---|---|
| 1FN | Valores atómicos (ya se cumplía) |
| 2FN | Separar Peliculas y Peliculas_Actores |
| 3FN | Crear Estudios y Actores con IDs numéricos |

Resultado final: 4 tablas en 3FN, sin datos repetidos ni dependencias parciales o transitivas.
