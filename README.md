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
| 🔧 **Tarjetas de Neumáticos** | Marca, modelo, medida, PSI (recomendado vs actual), profundidad de huella |
| 🛞 **Frenos y Discos** | Estado de balatas, tambores y discos con indicadores de desgaste |

---

## 🏗️ Estructura del Proyecto

```
lattex/
├── main.tex                    # 📄 Documento principal — estilos, colores, macros y configuración
├── page1.tex                   # 📝 Página 1 — Info general, luces de advertencia, gasolina y líquidos
├── page2.tex                   # 📝 Página 2 — Inspección de neumáticos (layout)
├── tirepage_components.tex     # 🧩 Componentes — TireCard, métricas PSI, barras de frenos
├── KodeMono-VariableFont_wght.ttf  # 🔤 Tipografía Kode Mono (variable)
├── top.png                     # 🖼️ Banner superior del formulario
├── logo.png                    # 🖼️ Logo del taller
├── Goodyear.png                # 🖼️ Logo de marca de llanta
└── *.png                       # 🖼️ Iconos de advertencia del tablero
```

---

## 🚀 Inicio Rápido

### Requisitos Previos

- **TeX Live** (2023+) o **MiKTeX** con XeLaTeX
- Fuente **Montserrat** instalada en el sistema
- Fuente **Kode Mono** (incluida en el repositorio)

### Compilación

```bash
# Compilar el documento con XeLaTeX
xelatex main.tex
```

> ⚡ **Nota:** Es necesario usar `xelatex` (no `pdflatex`) ya que el proyecto utiliza `fontspec` para manejar las tipografías del sistema.

---

## ✏️ Componentes Editables

A continuación se listan **todos** los campos que se pueden personalizar, organizados por archivo.

---

### `main.tex` — Colores globales

Los colores principales del formulario se definen aquí:

```latex
\definecolor{warningyellow}{HTML}{FCC01A}  % Amarillo de advertencia y elementos activos
\definecolor{trackgray}{HTML}{E6E6E6}      % Gris de las barras de progreso
\definecolor{oiltrack}{HTML}{E6E6E6}       % Gris para la barra de nivel de aceite
```

---

### `paginas/page1.tex` — Página 1

#### Información General del Vehículo

Edita directamente los valores dentro de cada `\begin{inputbox}`:

```latex
\begin{inputbox}VOLKSWAGEN TIGUAN 2026\end{inputbox}   % Modelo del vehículo
\begin{inputbox}JCZ-263-A\end{inputbox}                % Placas
\begin{inputbox}85,000\end{inputbox}                   % Kilometraje
\begin{inputbox}3N1BC13E38L592153\end{inputbox}        % Número de serie
\begin{inputbox}CAMBIO DE LLANTAS CON ALINEACIÓN Y BALANCEO\end{inputbox}  % Razón de ingreso
```

#### Chips de Luces Encendidas

Agrega o elimina etiquetas de texto libre que describen las luces activas:

```latex
\chip{Batería}\hspace{2mm}
\chip{Cinturón}\hspace{2mm}
\chip{Puertas abiertas}
```

#### Indicadores de Advertencia (Grid)

El último parámetro activa (`1`) o desactiva (`0`) cada icono:

```latex
\warniconij{col}{fila}{icono.png}{estado}
% Ejemplo:
\warniconij{0}{0}{engine.png}{1}    % ✅ Motor — encendida
\warniconij{1}{0}{oil.png}{0}       % ❌ Aceite — apagada
```

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

#### Nivel de Gasolina

```latex
\gasolinebar{4}  % 0=BAJO  1=1/4  2=MEDIO  3=3/4  4=LLENO
```

#### Inspección de Líquidos

```latex
\oillevelbar{2}                          % 0=DEBAJO DEL NIVEL  1=A NIVEL  2=ARRIBA DEL NIVEL
\oilcolorselector{0}                     % 0=Limpio  1=Medio  2=Quemado
\fluidselectorfour{1}{Anticongelante}    % primer arg: 0=N/A  1=A Nivel  2=Arriba del Nivel  3=Debajo del Nivel
\fluidselectorfour{3}{Dirección Hidraulica}
\fluidselectorfour{0}{Líquido de frenos}
```

#### Líquido Limpiaparabrisas

```latex
\yesnoselector{0}  % 0=SI seleccionado  1=NO seleccionado
```

---

### `paginas/page2.tex` — Página 2

#### Logo y Modelo de Llanta por Posición

Cambia el archivo de logo y el nombre del modelo para cada una de las cuatro ruedas:

```latex
\newcommand{\WheelLogoFileFrontRight}{Goodyear.png}
\newcommand{\WheelModelNameFrontRight}{WRANGLER ALL TERRAIN ADVENTURE W/KEVLAR 110T}

\newcommand{\WheelLogoFileRearRight}{Firestone.png}
\newcommand{\WheelModelNameRearRight}{WRANGLER ALL TERRAIN ADVENTURE W/KEVLAR 110T}

\newcommand{\WheelLogoFileFrontLeft}{Onyx.png}
\newcommand{\WheelModelNameFrontLeft}{WRANGLER ALL TERRAIN ADVENTURE W/KEVLAR 110T}

\newcommand{\WheelLogoFileRearLeft}{Continental.png}
\newcommand{\WheelModelNameRearLeft}{WRANGLER ALL TERRAIN ADVENTURE W/KEVLAR 110T}
```

#### Métricas por Llanta (`\SimpleWheelBlock`)

Cada llamada acepta: `{posición}{logo}{modelo}{medida}{PSI}{profundidad}{desgaste disco}{desgaste balata}`

```latex
\SimpleWheelBlock{Delantera Derecha}{\WheelLogoFileFrontRight}{\WheelModelNameFrontRight}
  {315/35/R21}  % Medida
  {25}           % PSI actual
  {3 mm}         % Profundidad de banda
  {9 mm}         % Desgaste de discos
  {8 mm}         % Desgaste de balatas/tambores
```

#### Observaciones de Llantas

```latex
\renewcommand{\WheelObservacionesTexto}{Escribe aquí tus observaciones de llantas.}
% Si se deja vacío, se muestra el texto de placeholder en gris.
```

#### Sistema de Suspensión

El primer argumento selecciona el estado: `0=N/A  1=Buena  2=Regular  3=Mala`

```latex
\SuspensionSelector{0}{Baleros de rueda / Delanteros y Traseros}{CON MASA}
\SuspensionSelector{3}{Cremallera / Caja de Dirección}{FUGA DE ACEITE}
\SuspensionSelector{3}{Horquillas, Rótulas o articulaciones}{CAMBIO SUPERIOR E INFERIOR}
```

#### Barra Estabilizadora (fila adicional)

```latex
\newcommand{\SuspensionExtraTitulo}{Barra estabilizadora y sus componentes}
\newcommand{\SuspensionExtraEstado}{0}   % 0=N/A  1=Buena  2=Regular  3=Mala
\newcommand{\SuspensionExtraObservacionesTexto}{CON MASA, FUGA DE ACEITE, CAMBIO SUPERIOR E INFERIOR.}
```

#### Inspección de Batería

```latex
\newcommand{\BatteryEstado}{2}              % 0=N/A  1=Buena  2=Regular  3=Mala
\newcommand{\BatteryVoltajeValor}{12}       % Valor numérico del voltaje (v)
\newcommand{\BatteryComentariosTexto}{}     % Texto libre de comentarios
```

---

### `paginas/page3.tex` — Página 3

#### Estados de Amortiguadores y Bases

Cada variable acepta: `0=sin seleccionar  1=Buena  2=Regular  3=Mala`

```latex
% Amortiguadores
\newcommand{\ShockAmortDelDerEstado}{1}   % Delantera Derecha
\newcommand{\ShockAmortDelIzqEstado}{2}   % Delantera Izquierda
\newcommand{\ShockAmortTraDerEstado}{3}   % Trasera Derecha
\newcommand{\ShockAmortTraIzqEstado}{1}   % Trasera Izquierda

% Bases
\newcommand{\ShockBaseDelDerEstado}{0}    % Delantera Derecha
\newcommand{\ShockBaseDelIzqEstado}{0}    % Delantera Izquierda
\newcommand{\ShockBaseTraDerEstado}{0}    % Trasera Derecha
\newcommand{\ShockBaseTraIzqEstado}{0}    % Trasera Izquierda
```

#### Cierre de Inspección

```latex
\ShockClosureCard{REVISADOR POR}{Señor mecánico juanito}   % Nombre del técnico
\ShockClosureCard{SUCURSAL}{Matriz lázaro cárdenas}        % Nombre de la sucursal
```

#### Fecha de Registro

```latex
{\fontsize{7}{8.4}\selectfont\color{black} Fecha de registro: Vie, 20 de febrero 2026}
% Edita el texto de fecha directamente en esta línea.
```

---

## 🎨 Personalización Rápida

### Colores

Los colores principales están definidos en `main.tex` y se pueden ajustar fácilmente:

```latex
\definecolor{warningyellow}{HTML}{FCC01A}  % Amarillo de advertencia
\definecolor{trackgray}{HTML}{E6E6E6}      % Gris de las barras
\definecolor{oiltrack}{HTML}{E6E6E6}       % Gris para la barra de aceite
```

---

## 🛞 Componentes UI

### Tarjeta de Neumáticos (TireCard — `tirepage_components.tex`)

Cada neumático se documenta con una tarjeta completa:

```latex
\TireCard{goodyear.png}{WRANGLER ALL TERRAIN ADVENTURE W/KEVLAR 110T}
  {315/35R21}       % Medida
  {210}              % Índice de velocidad
  {210}              % Índice de carga
  {{35}{25}}         % PSI {recomendado}{actual}
  {3 mm}             % Profundidad
  {{BUENA (>9MM)}{8 mm}}   % Balatas {estado}{desgaste}
  {{BUENA (>9MM)}{9 mm}}   % Discos  {estado}{desgaste}
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
