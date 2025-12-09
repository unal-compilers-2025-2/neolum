# NEOLUM

**Visualizador de Autómatas - Automata Visualizer**

NEOLUM es una aplicación web interactiva para visualizar, diseñar y analizar autómatas finitos. Permite convertir expresiones regulares en autómatas (NFA-λ, NFA, DFA) y validar cadenas de entrada, todo con una interfaz moderna y educativa.

## Características

- **Conversión de Expresiones Regulares**: Transforma expresiones regulares en autómatas usando el algoritmo de construcción de Thompson
- **Múltiples Representaciones**: Visualiza NFA-λ (con transiciones épsilon), NFA y DFA
- **Validación de Cadenas**: Verifica si una cadena es aceptada por el autómata generado
- **Entrada Flexible**: Soporta expresiones regulares y listas de aristas (edge lists)
- **Visualización Interactiva**: Gráficos claros con estados, transiciones y símbolos
- **Tema oscuro**: Tema moderno con efectos de neón cian y magenta

## Demo

La aplicación permite:

1. Ingresar una expresión regular (ej: `(a|b)*abb`)
2. Generar automáticamente el NFA-λ, NFA y DFA correspondientes
3. Visualizar cada etapa de la conversión
4. Validar cadenas de entrada contra el autómata

También soporta entrada mediante lista de aristas:

```
q0, a, q1
q1, b, q2
q2, b, q3
accept: q3
```

## Ejemplos de Expresiones Regulares

| Expresión | Descripción |
|-----------|-------------|
| `(a\|b)*abb` | Cadenas que terminan en "abb" |
| `a*b*` | Cero o más a's seguidas de cero o más b's |
| `(ab)+` | Una o más repeticiones de "ab" |

## Tecnologías

- **React** - Framework de interfaz de usuario
- **TypeScript** - Tipado estático
- **Tailwind CSS** - Estilos y diseño responsivo
- **Lucide React** - Iconos
- **Algoritmos Implementados**:
  - Construcción de Thompson (Regex → NFA-λ)
  - Eliminación de transiciones épsilon (NFA-λ → NFA)
  - Construcción de subconjuntos (NFA → DFA)

## Instalación y Uso

### Opción 1: Uso Directo (Recomendado)

La aplicación está lista para usar directamente en tu navegador. Simplemente abre el archivo HTML o despliégala en cualquier servidor web estático.

### Opción 2: Desarrollo Local

```bash
# Clonar el repositorio
git clone https://github.com/tuusuario/neolum.git

# Instalar dependencias
cd neolum
npm install

# Ejecutar en modo desarrollo
npm run dev

# Construir para producción
npm run build
```

## Cómo Usar

1. **Selecciona el Modo de Entrada**:
   - "Expresión Regular" para convertir regex a autómatas
   - "Lista de Aristas" para definir transiciones manualmente

2. **Ingresa tu Expresión o Lista**:
   - Usa operadores: `*` (Kleene), `+` (Plus), `?` (Opcional), `|` (Unión), `()` (Agrupación)
   - Ejemplo: `(a|b)*abb`

3. **Genera los Autómatas**:
   - Haz clic en "Generar Autómatas"
   - Navega entre NFA-λ, NFA y DFA usando las pestañas

4. **Valida Cadenas** (opcional):
   - Ingresa una cadena de prueba
   - El sistema indicará si es aceptada o rechazada

## Algoritmos Implementados

### 1. Construcción de Thompson

Convierte expresiones regulares en NFA-λ mediante fragmentos básicos:

- **Símbolo básico**: Crea dos estados con una transición
- **Concatenación**: Conecta fragmentos con transiciones λ
- **Unión**: Crea estados iniciales/finales con bifurcaciones λ
- **Clausura de Kleene**: Añade bucles y transiciones opcionales λ

### 2. Eliminación de Épsilon

Transforma NFA-λ a NFA eliminando transiciones λ:

- Calcula la clausura épsilon de cada estado
- Crea transiciones directas para cada símbolo del alfabeto
- Actualiza estados de aceptación según clausuras

### 3. Construcción de Subconjuntos

Convierte NFA en DFA determinístico:

- Cada estado del DFA representa un conjunto de estados del NFA
- Construye transiciones determinísticas
- Simplifica nombres de estados

**NEOLUM** - Visualiza, aprende y experimenta con autómatas finitos
