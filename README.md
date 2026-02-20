<p align="center">
  <img src="imagenes/logo.png" alt="LaTTeX Logo" width="280"/>
</p>

<h1 align="center">🏎️ LaTTeX — Inspección Vehicular Profesional</h1>

<p align="center">
  <strong>Formularios de inspección multi-punto para talleres automotrices, generados con LaTeX.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/LaTeX-XeLaTeX-008080?style=for-the-badge&logo=latex&logoColor=white" alt="XeLaTeX"/>
  <img src="https://img.shields.io/badge/TikZ-Gráficos_Vectoriales-blue?style=for-the-badge" alt="TikZ"/>
  <img src="https://img.shields.io/badge/Idioma-Español-red?style=for-the-badge" alt="Español"/>
  <img src="https://img.shields.io/badge/Licencia-Uso_Libre-green?style=for-the-badge" alt="Licencia"/>
</p>

---

## 📋 ¿Qué es LaTTeX?

**LaTTeX** es un sistema de generación de formularios de inspección vehicular multi-punto, diseñado con **LaTeX** para producir documentos PDF de calidad profesional. Ideal para talleres mecánicos, centros de servicio automotriz y distribuidores de llantas.

> *"vergueado no, vergas si"* — Mike, 2026

---

## ✨ Características

| Característica | Descripción |
|---|---|
| 🚗 **Información General** | Modelo, placas, kilometraje, número de serie y razón de ingreso |
| ⚠️ **Luces de Advertencia** | Grid interactivo con 17 indicadores del tablero (motor, aceite, batería, ABS, etc.) |
| ⛽ **Nivel de Gasolina** | Barra visual con 5 niveles: Bajo, 1/4, Medio, 3/4, Lleno |
| 🛢️ **Inspección de Líquidos** | Nivel y color de aceite, anticongelante, dirección hidráulica, líquido de frenos |
| 🔧 **Tarjetas de Neumáticos** | Marca, modelo, medida, PSI, índices de velocidad/carga y profundidad de huella |
| 🛞 **Frenos y Discos** | Estado de balatas, tambores y discos con indicadores de desgaste |
| 🔩 **Sistema de Suspensión** | Estado de baleros, cremallera, horquillas y barra estabilizadora |
| 🔋 **Batería** | Condición general, voltaje y comentarios adicionales |
| 🏗️ **Amortiguadores y Bases** | Inspección delantera y trasera (izquierda y derecha) |
| 📋 **Cierre de Inspección** | Nombre del revisor, sucursal y fecha de registro |

---

## 🏗️ Estructura del Proyecto

```
lattex/
├── main.tex                        # 📄 Documento principal — paquetes, colores, macros y configuración
├── configuraciones/
│   ├── rutas.tex                   # 🗺️ Rutas centralizadas (\graphicspath)
│   └── KodeMono-VariableFont_wght.ttf  # 🔤 Tipografía Kode Mono (variable)
├── paginas/
│   ├── page1.tex                   # 📝 Página 1 — Info general, luces de advertencia, gasolina y líquidos
│   ├── page2.tex                   # 📝 Página 2 — Llantas, frenos, suspensión y batería
│   ├── page3.tex                   # 📝 Página 3 — Amortiguadores, bases y cierre de inspección
│   └── tirepage_components.tex     # 🧩 Componentes alternativos de tarjeta de llanta (TFTireCard)
└── imagenes/
    ├── logo.png                    # 🖼️ Logo del taller
    ├── top.png                     # 🖼️ Banner superior del formulario
    ├── botton.png                  # 🖼️ Banner inferior del formulario
    ├── carro.png                   # 🖼️ Diagrama del vehículo (vista superior)
    ├── Goodyear.png                # 🖼️ Logo de marca de llanta
    ├── Firestone.png               # 🖼️ Logo de marca de llanta
    ├── Onyx.png                    # 🖼️ Logo de marca de llanta
    ├── Continental.png             # 🖼️ Logo de marca de llanta
    └── *.png                       # 🖼️ Iconos de advertencia del tablero (17 iconos)
```

---

## 📄 Contenido por Página

### Página 1 — `paginas/page1.tex`
- **Información General del Vehículo:** Modelo, placas, kilometraje, número de serie y razón de ingreso
- **Luces de Advertencia:** Grid con 17 iconos del tablero, activables individualmente
- **Nivel de Gasolina:** Barra visual de 5 niveles
- **Inspección de Líquidos:** Nivel y color de aceite, anticongelante, dirección hidráulica, líquido de frenos y limpiaparabrisas

### Página 2 — `paginas/page2.tex`
- **Llantas y Frenos:** 4 tarjetas de neumáticos (Delantera/Trasera Derecha/Izquierda) con marca, modelo, medida, PSI, índices y profundidad; frenos, discos y tambores
- **Observaciones:** Caja de texto libre
- **Sistema de Suspensión:** Baleros, cremallera/caja de dirección, horquillas/rótulas y barra estabilizadora
- **Batería:** Condición general (N/A / Buena / Regular / Mala), voltaje en volts y comentarios

### Página 3 — `paginas/page3.tex`
- **Amortiguadores y Bases:** Tabla de inspección delantera derecha/izquierda y trasera derecha/izquierda, con estado Buena/Regular/Mala para amortiguadores y bases por separado
- **Cierre de Inspección:** Tarjetas con nombre del revisor y sucursal, fecha de registro

---

## 🚀 Inicio Rápido

### Requisitos Previos

- **TeX Live** (2023+) o **MiKTeX** con XeLaTeX
- Fuente **Montserrat** instalada en el sistema
- Fuente **Kode Mono** (incluida en `configuraciones/`)

### Compilación

```bash
# Compilar el documento con XeLaTeX
xelatex main.tex
```

> ⚡ **Nota:** Es necesario usar `xelatex` (no `pdflatex`) ya que el proyecto utiliza `fontspec` para manejar las tipografías del sistema.

---

## 🎨 Personalización

### Colores

Los colores principales están definidos en `main.tex` y se pueden ajustar fácilmente:

```latex
\definecolor{warningyellow}{HTML}{FCC01A}  % Amarillo de advertencia
\definecolor{trackgray}{HTML}{E6E6E6}      % Gris de las barras
\definecolor{oiltrack}{HTML}{E6E6E6}       % Gris para la barra de aceite
```

### Datos del Vehículo

Los datos se editan directamente en `paginas/page1.tex`:

```latex
% Modelo del vehículo
VOLKSWAGEN TIGUAN 2026

% Placas
JCZ-263-A

% Kilometraje
85,000
```

### Indicadores de Advertencia

Cada luz del tablero se activa (`1`) o desactiva (`0`). Los argumentos son: columna, fila, ícono, estado:

```latex
\warniconij{0}{0}{engine.png}{1}    % ✅ Encendida
\warniconij{1}{0}{oil.png}{0}       % ❌ Apagada
```

### Nivel de Gasolina

```latex
\gasolinebar{4}  % 0=BAJO, 1=1/4, 2=MEDIO, 3=3/4, 4=LLENO
```

### Líquidos

```latex
\oillevelbar{2}        % 0=DEBAJO DEL NIVEL, 1=A NIVEL, 2=ARRIBA DEL NIVEL
\oilcolorselector{0}   % 0=Limpio, 1=Medio, 2=Quemado
\fluidselectorfour{1}{Anticongelante}  % 0=N/A, 1=A Nivel, 2=Arriba del Nivel, 3=Debajo del Nivel
\yesnoselector{0}      % 0=SI, 1=NO  (limpiaparabrisas)
```

### Tarjeta de Neumáticos

Cada posición de llanta se define con `\SimpleWheelBlock` en `paginas/page2.tex`:

```latex
\SimpleWheelBlock{Delantera Derecha}{Goodyear.png}{WRANGLER ALL TERRAIN ADVENTURE W/KEVLAR 110T}
  {315/35/R21}   % Medida
  {25}            % PSI
  {3 mm}          % Profundidad de banda
  {9 mm}          % Desgaste de discos
  {8 mm}          % Desgaste de balatas/tambores
```

Los logos de marca y modelo se configuran con variables al inicio de `page2.tex`:

```latex
\newcommand{\WheelLogoFileFrontRight}{Goodyear.png}
\newcommand{\WheelModelNameFrontRight}{WRANGLER ALL TERRAIN ADVENTURE W/KEVLAR 110T}
```

### Sistema de Suspensión

```latex
\SuspensionSelector{1}{Baleros de rueda / Delanteros y Traseros}{observaciones aquí}
% Estado: 0=N/A, 1=Buena, 2=Regular, 3=Mala
```

### Batería

```latex
\newcommand{\BatteryEstado}{2}         % 0=N/A, 1=Buena, 2=Regular, 3=Mala
\newcommand{\BatteryVoltajeValor}{12}  % Voltaje en volts
```

### Amortiguadores

```latex
\newcommand{\ShockAmortDelDerEstado}{1}  % 1=Buena, 2=Regular, 3=Mala
\newcommand{\ShockBaseDelDerEstado}{0}   % 0=sin selección
```

### Cierre de Inspección

```latex
\ShockClosureCard{REVISADOR POR}{Señor mecánico juanito}
\ShockClosureCard{SUCURSAL}{Matriz lázaro cárdenas}
```

---

## 🛞 Componentes UI

### Luces de Advertencia

El formulario incluye **17 iconos** del tablero del vehículo ubicados en `imagenes/`:

| Icono | Indicador | | Icono | Indicador |
|---|---|---|---|---|
| `engine.png` | Motor | | `abs.png` | ABS |
| `oil.png` | Aceite | | `tractionControl.png` | Control de tracción |
| `battery.png` | Batería | | `doors.png` | Puertas |
| `air.png` | Aire | | `immobilizer.png` | Inmovilizador |
| `throttle.png` | Acelerador | | `brake.png` | Frenos |
| `celsius.png` | Temperatura | | `brakePark.png` | Freno de mano |
| `maintenance.png` | Mantenimiento | | `tire.png` | Neumáticos |
| `lighbulb.png` | Luces | | `windshield-washer.png` | Limpiaparabrisas |
| `steering-wheel.png` | Dirección | | | |

### Selector de 4 estados (Suspensión / Líquidos)

Reutilizable para suspensión y líquidos; muestra círculos de color según el estado:

- 🔵 **N/A** — azul
- 🟢 **Buena / A Nivel** — verde
- 🟡 **Regular / Arriba del Nivel** — amarillo
- 🔴 **Mala / Debajo del Nivel** — rojo

### Tarjeta Alternativa de Neumáticos (`tirepage_components.tex`)

`paginas/tirepage_components.tex` define `\TFTireCard`, un diseño alternativo de tarjeta con header azul/gris, 5 columnas de métricas y filas de frenos en verde:

```latex
\input{paginas/tirepage_components}
\TFTireCard{Delantera Derecha}
```

---

## 📦 Paquetes LaTeX Utilizados

| Paquete | Uso |
|---|---|
| `geometry` | Configuración de márgenes |
| `graphicx` | Inclusión de imágenes PNG |
| `fontspec` | Fuentes del sistema (Montserrat) y variables (Kode Mono) |
| `tcolorbox` | Cajas de formulario con bordes redondeados |
| `xcolor` | Definición de colores personalizados |
| `tabularx` | Tablas responsivas |
| `tikz` | Gráficos vectoriales (barras, selectores, iconos) |

---

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas! Si tienes ideas para mejorar el formulario:

1. Haz un **fork** del repositorio
2. Crea una rama con tu mejora (`git checkout -b feature/mi-mejora`)
3. Haz commit de tus cambios (`git commit -m 'Agregar mi mejora'`)
4. Haz push a la rama (`git push origin feature/mi-mejora`)
5. Abre un **Pull Request**

---

<p align="center">
  Hecho con ❤️, LaTeX y muchas ganas de que quede <strong>espectacular</strong>
</p>
