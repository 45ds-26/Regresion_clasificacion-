# Construcción, validación y análisis de modelos lineales

Actividad colaborativa de Machine Learning Supervisado: un problema de **regresión** y uno de **clasificación**, desarrollados sobre datasets públicos reales con la misma naturaleza de datos (medidas corporales de animales usadas para predecir un rasgo biológico), lo que permite un contraste metodológico limpio entre ambos enfoques.

## Estructura del proyecto

| Bloque | Problema | Dataset | Variable objetivo |
|---|---|---|---|
| I | Regresión | [Fish Market](https://www.kaggle.com/datasets/aungpyaeap/fish-market) | `Weight` (peso en gramos, continua) |
| II | Clasificación | [Palmer Penguins](https://allisonhorst.github.io/palmerpenguins/) | `species` (Adelie / Chinstrap / Gentoo) |
| III | — | Análisis comparativo final entre ambos bloques | — |

Cada bloque sigue la misma metodología: modelo base (**Decision Tree**) → ingeniería de características (al menos 2 técnicas) → modelo mejorado (**Random Forest**) → comparación de métricas antes/después.

## Resultados clave

**Bloque I — Regresión (Fish Market)**

| Modelo | MAE (g) | RMSE (g) | R² |
|---|---|---|---|
| Base — Decision Tree | 58.81 | 96.71 | 0.930 |
| Mejorado — Random Forest + FE | 38.28 | 64.90 | 0.969 |

**Bloque II — Clasificación (Palmer Penguins)**

| Modelo | Accuracy (test) | Accuracy (CV 5-fold) |
|---|---|---|
| Base — Decision Tree | 1.000 | 0.971 ± 0.019 |
| Mejorado — Random Forest + FE | 1.000 | 0.988 ± 0.006 |

En regresión, el feature engineering (transformación log + variable de volumen) redujo el error de forma directa y medible. En clasificación, ambos modelos ya alcanzaban accuracy perfecto en el split de prueba, así que la mejora real solo se evidencia en la validación cruzada (mayor estabilidad, menor varianza entre folds).


## Cómo ejecutar el notebook

El notebook carga ambos datasets directamente desde GitHub, por lo que corre sin archivos adicionales (local o en Google Colab):

```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
jupyter notebook actividad_regresion_clasificacion.ipynb
```

## Fuentes de datos

- Pyae, A. (n.d.). *Fish market* [Data set]. Kaggle. https://www.kaggle.com/datasets/aungpyaeap/fish-market
- Horst, A. M., Hill, A. P., & Gorman, K. B. (2020). *palmerpenguins: Palmer Archipelago (Antarctica) penguin data* (R package version 0.1.0) [Data set]. https://allisonhorst.github.io/palmerpenguins/
- Gorman, K. B., Williams, T. D., & Fraser, W. R. (2014). Ecological sexual dimorphism and environmental variability within a community of Antarctic penguins (genus *Pygoscelis*). *PLoS ONE*, *9*(3), e90081. https://doi.org/10.1371/journal.pone.0090081

## Autor

David Santiago Díaz Pradilla
