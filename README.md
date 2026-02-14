# 🧹 Retail Store Sales - Data Cleaning Project

## 📋 Descripción del Proyecto

Este proyecto tiene como objetivo limpiar, transformar y preparar un dataset de ventas minoristas que contiene múltiples problemas de calidad de datos. El dataset simula escenarios reales encontrados en sistemas de producción, convirtiéndolo en un caso de estudio ideal para practicar técnicas de Data Cleaning y Data Wrangling.

## 📊 Sobre el Dataset

**Fuente:** [Kaggle - Retail Store Sales: Dirty for Data Cleaning](https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning)

**Dimensiones:** 12,575 transacciones × 11 variables

**Período temporal:** Enero 2022 - Enero 2025

### Variables del Dataset

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `Transaction ID` | String | Identificador único de la transacción (formato: TXN_XXXXXXX) |
| `Customer ID` | String | Identificador del cliente (formato: CUST_XX) |
| `Category` | String | Categoría del producto vendido |
| `Item` | String | Nombre específico del producto |
| `Price Per Unit` | Float | Precio unitario del producto |
| `Quantity` | Float | Cantidad de unidades compradas |
| `Total Spent` | Float | Monto total de la transacción |
| `Payment Method` | String | Método de pago utilizado |
| `Location` | String | Ubicación de la compra (Online/In-store) |
| `Transaction Date` | String | Fecha de la transacción |
| `Discount Applied` | Boolean | Indica si se aplicó descuento |

### Categorías de Productos

El dataset incluye 8 categorías principales:

- **Furniture** (Muebles) - 1,591 transacciones
- **Electric household essentials** (Electrodomésticos esenciales) - 1,591 transacciones
- **Food** (Alimentos) - 1,588 transacciones
- **Milk Products** (Productos lácteos) - 1,584 transacciones
- **Butchers** (Carnicería) - 1,568 transacciones
- **Beverages** (Bebidas) - 1,567 transacciones
- **Computers and electric accessories** (Computadoras y accesorios) - 1,558 transacciones
- **Patisserie** (Pastelería) - 1,528 transacciones

### Métodos de Pago

- **Cash** (Efectivo): 34.3%
- **Digital Wallet** (Billetera Digital): 33.0%
- **Credit Card** (Tarjeta de Crédito): 32.7%

### Ubicaciones

- **Online**: 50.5%
- **In-store**: 49.5%

## 🔍 Problemas de Calidad de Datos Identificados

### 1. **Valores Faltantes (Missing Values)**

| Variable | Registros Faltantes | Porcentaje |
|----------|---------------------|------------|
| `Discount Applied` | 4,199 | 33.39% |
| `Item` | 1,213 | 9.65% |
| `Price Per Unit` | 609 | 4.84% |
| `Quantity` | 604 | 4.80% |
| `Total Spent` | 604 | 4.80% |

**Características:**
- Los valores faltantes en `Price Per Unit`, `Quantity` y `Total Spent` están correlacionados
- Existen 1,213 transacciones con categoría definida pero sin nombre de item
- Alto porcentaje de valores faltantes en `Discount Applied` (33%)

### 2. **Datos Parcialmente Incompletos**

- **1,213 registros** tienen categoría asignada pero el campo `Item` está vacío
- Algunos registros tienen precio pero no cantidad, o viceversa

### 3. **Tipo de Datos Inconsistente**

- `Transaction Date` está almacenada como string en lugar de datetime
- `Discount Applied` contiene valores booleanos mixtos (True/False/NaN)

### 4. **Estadísticas Descriptivas**

**Variables Numéricas:**

| Métrica | Price Per Unit | Quantity | Total Spent |
|---------|----------------|----------|-------------|
| Media | $23.37 | 5.54 unidades | $129.65 |
| Desv. Est. | $10.74 | 2.86 | $94.75 |
| Mínimo | $5.00 | 1 | $5.00 |
| Máximo | $41.00 | 10 | $410.00 |

### 5. **Puntos Positivos (Buena Calidad)**

✅ No hay duplicados en Transaction IDs
✅ No hay valores negativos o cero en variables numéricas
✅ La fórmula `Total Spent = Price Per Unit × Quantity` es consistente donde hay datos completos
✅ Todas las fechas son válidas (rango: 2022-2025)
✅ Distribución equilibrada entre canales y métodos de pago

## 🎯 Objetivos del Proyecto

1. **Limpieza de Datos:**
   - Manejo de valores faltantes mediante estrategias apropiadas
   - Imputación o eliminación de registros incompletos
   - Normalización de formatos de datos

2. **Transformación:**
   - Conversión de tipos de datos (fechas, booleanos)
   - Creación de variables derivadas (día de la semana, mes, año)
   - Categorización de variables continuas si es necesario

3. **Validación:**
   - Verificación de integridad referencial
   - Validación de reglas de negocio
   - Detección de outliers

4. **Análisis Exploratorio:**
   - Patrones de compra por categoría
   - Tendencias temporales
   - Análisis de métodos de pago y ubicación
   - Impacto de descuentos en las ventas

## 🛠️ Tecnologías Utilizadas

- **Python 3.x**
- **Pandas** - Manipulación y análisis de datos
- **NumPy** - Operaciones numéricas
- **Matplotlib/Seaborn** - Visualización de datos
- **Jupyter Notebook** - Desarrollo interactivo

## 📁 Estructura del Proyecto

```
retail-sales-cleaning/
│
├── data/
│   ├── raw/                    # Datos originales sin procesar
│   │   └── retail_store_sales.csv
│   └── processed/              # Datos limpios
│       └── retail_store_sales_clean.csv
│
├── notebooks/
│   ├── 01_exploratory_analysis.ipynb
│   ├── 02_data_cleaning.ipynb
│   └── 03_final_analysis.ipynb
│
├── src/
│   ├── data_cleaning.py        # Funciones de limpieza
│   └── utils.py                # Utilidades generales
│
├── reports/
│   ├── figures/                # Gráficos y visualizaciones
│   └── data_quality_report.md  # Reporte de calidad
│
├── requirements.txt            # Dependencias del proyecto
└── README.md                   # Este archivo
```

## 🚀 Instalación y Uso

### Prerequisitos

```bash
Python 3.8+
pip o conda
```

### Instalación

1. Clonar el repositorio:
```bash
git clone https://github.com/tu-usuario/retail-sales-cleaning.git
cd retail-sales-cleaning
```

2. Crear un entorno virtual:
```bash
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
```

3. Instalar dependencias:
```bash
pip install -r requirements.txt
```

4. Descargar el dataset:
- Descargar desde [Kaggle](https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning)
- Colocar `retail_store_sales.csv` en `data/raw/`

### Ejecución

```bash
jupyter notebook notebooks/01_exploratory_analysis.ipynb
```

## 📈 Resultados Esperados

Al finalizar el proyecto, se espera obtener:

- ✅ Dataset limpio y validado listo para análisis
- ✅ Documentación completa de decisiones de limpieza
- ✅ Visualizaciones de patrones y tendencias
- ✅ Reporte de calidad de datos antes/después
- ✅ Código reutilizable para procesos ETL similares

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Por favor:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📝 Licencia

Este proyecto utiliza datos públicos de Kaggle. El código está disponible bajo licencia MIT.

## 👤 Autor

**Tu Nombre**
- GitHub: [@tu-usuario](https://github.com/tu-usuario)
- LinkedIn: [Tu Perfil](https://linkedin.com/in/tu-perfil)

## 🙏 Agradecimientos

- Dataset original por [Ahmed Mohamed](https://www.kaggle.com/ahmedmohamed2003) en Kaggle
- Comunidad de Data Science por recursos y mejores prácticas

---

⭐ Si este proyecto te fue útil, no olvides darle una estrella en GitHub!
