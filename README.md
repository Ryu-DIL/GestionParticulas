# Gestor de Fichas — versión con interfaz gráfica

Evolución con interfaz gráfica de **[Particulas_gestion](https://github.com/Ryu-DIL/Particulas_gestion)**, el gestor de fichas de partículas en C++ por consola. Esta versión reimplementa el mismo motor —catálogos configurables, familias y grupos, notación científica o de coma fija, búsquedas— como una aplicación web de un único archivo HTML, con pestañas, formularios y botones en lugar de un menú numerado por teclado.

> 🔗 ¿Buscas la versión original en C++ (consola, ficheros `.ini`/`.txt`)? Está en **[Particulas_gestion](https://github.com/Ryu-DIL/Particulas_gestion)**. Este repositorio es su evolución con interfaz gráfica.

## ✨ Qué es

Un sistema de "fichas" de catálogo configurable: define ocho campos (Nombre, Símbolo, Masa, Carga, Familia, Grupo, País, Año) y reetiqueta cada uno según el dominio que quieras catalogar. Incluye dos catálogos de ejemplo listos para usar:

- **Partículas elementales** — notación científica, familias Fermiones/Bosones (electrón, quark top, bosón W+).
- **Personajes memorables** — notación de coma fija, el mismo motor aplicado a un dominio completamente distinto.

## 🖥️ Cómo usarlo

No requiere instalación ni dependencias: es HTML, CSS y JavaScript en un único archivo.

- **Abrir directamente**: descarga `index.html` y ábrelo con cualquier navegador.
- **Servirlo en local** (opcional):
  ```bash
  python3 -m http.server 8000
  ```
  y visita `http://localhost:8000`.
- **GitHub Pages**: activa Pages en *Settings → Pages*, apunta a la rama `main` y la carpeta raíz. Al llamarse `index.html`, se sirve automáticamente.

Los datos viven en memoria mientras usas la app; para conservarlos entre sesiones, expórtalos a `.json` desde la pestaña **Catálogo**.

## 🧩 Funcionalidades

| Pestaña | Qué permite |
|---|---|
| **Fichas** | Listar en tarjetas, filtrar por nombre/símbolo o por familia, crear, editar y borrar fichas |
| **Buscar** | Nombre exacto, nombre contiene, masa menor que, por familia, por familia y grupo |
| **Familias / Grupos** | Añadir categorías nuevas y eliminar las que no estén en uso |
| **Configuración** | Renombrar las ocho etiquetas de campo y elegir notación científica o de coma fija |
| **Catálogo** | Cargar un catálogo de ejemplo, crear uno en blanco, e importar/exportar como `.json` |

## 🔄 Diferencias con la versión original

| Original (C++, consola) | Esta versión (web, UI) |
|---|---|
| Menú numerado, entrada por teclado | Pestañas, botones y formularios |
| Configuración en `menu.ini` / `particulasraras.ini` | Pestaña Configuración, con validación en vivo |
| Datos en `particulas.txt` / `particulasraras.txt` | Un único archivo `.json` exportable/importable |
| Familias y Grupos fijos al crear el catálogo | Se pueden añadir en cualquier momento |
| Aviso de guardado pendiente al salir | Aviso de "cambios sin exportar" antes de cambiar de catálogo |

## 📦 Formato de catálogo (`.json`)

```json
{
  "catalogo": "Partículas elementales",
  "formato": "cientifica",
  "etiquetas": {
    "nombre": "Nombre de la partícula", "simbolo": "Símbolo",
    "masa": "Masa (eV/c²)", "carga": "Carga",
    "familia": "Familia", "grupo": "Grupo",
    "pais": "País de descubrimiento", "anyo": "Año de descubrimiento"
  },
  "familias": ["Fermiones", "Bosones"],
  "grupos": ["Leptones", "Quarks", "Gauge"],
  "fichas": [
    { "nombre": "Electrón", "simbolo": "e", "masa": 511000, "carga": -1,
      "familia": "Fermiones", "grupo": "Leptones", "pais": "Reino Unido", "anyo": 1896 }
  ]
}
```

`masa: -1` y `anyo: -1` representan "Desconocido", igual que en los ficheros `.txt` originales.

## 📁 Estructura del repositorio

```
.
├── index.html   # aplicación completa (HTML + CSS + JS)
└── README.md
```
