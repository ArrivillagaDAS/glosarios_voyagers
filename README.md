# Gestión de Cambio - Grupos Dinámicos

Este repositorio establece el flujo de trabajo colaborativo y la asignación de responsabilidades para la gestión semanal de glosarios técnicos y conceptuales.

## Flujo de Trabajo

1. Para iniciar a trabajar, realizar un **fork** del repositorio principal.
2. Clonar el repositorio bifurcado en una carpeta local.
3. Cada equipo debe trabajar sobre la rama asignada según el glosario que le corresponde, asegurándose de revisar y verificar que se encuentran en dicha rama antes de realizar cualquier cambio.

## Estructura del Repositorio y Ramas

El control de versiones y el desarrollo se estructuran bajo el siguiente árbol de ramas:

```
main
└── dev
    ├── ser
    ├── software
    └── ingles
```

### Estructura de directorios

```
├── ingles/
│   ├── equipo1/
│   ├── equipo2/
│   └── equipo3/
├── ser/
│   ├── equipo1/
│   ├── equipo2/
│   └── equipo3/
└── software/
    ├── equipo1/
    ├── equipo2/
    └── equipo3/
```

## Asignación de Equipos de Trabajo

**Team 1:**
- Brandon Estiben Ixén
- Edgar Manolo Polanco Sánchez
- Carlos Elias Tzoy Velasco
- Selvin Eladio Lem Ical
- Jakelin Mishel Quino Martinez
- Pablo López Monzón
- Cleidy Priscilia Pérez Casia
- Marco Antonio Canux Raquec

**Team 2:**
- Allison Rocio Vargas Mejias
- Irma Yaneht Arias Garcia
- Maria José Montepeque Zet
- Stefani Fabiola Sánchez Pérez
- Ángela Sofia de la Cruz Arrivillaga
- Daniel Aguilar Rodriguez
- Sergio Ricardo Ajú Miranda
- Jose Luis Tot Herrera

**Team 3:**
- Lucas Samuel Pajarito Surek
- Lester Alexander Garcia Felipe
- Anderson Oloroso
- Joseph Fernando Ramirez Montenegro
- Evelyn Noemi Barrios Méndez
- Wilder Fernando Elias Cat Colaj
- Byron Lorenzo Ajcet Ignacio

## Cronograma y Rotación de Glosarios

| Semana   | Team 1              | Team 2              | Team 3              |
|----------|----------------------|----------------------|----------------------|
| Semana 1 | Glosario: Ser         | Glosario: Software    | Glosario: Inglés     |
| Semana 2 | Glosario: Inglés      | Glosario: Ser         | Glosario: Software   |
| Semana 3 | Glosario: Software    | Glosario: Inglés      | Glosario: Ser        |

> **Fecha límite de entrega:** Todos los jueves de cada semana correspondiente.

## Estructura de Contenido por Glosario

- **Glosario Ser:** Término, descripción y un ejemplo de aplicación.
- **Glosario Software:** Término, descripción y ejemplo (si aplica).
- **Glosario Inglés:** Término, traducción, descripción en inglés y en español, y ejemplo en inglés.

> **Aporte individual:** Cada integrante debe aportar obligatoriamente dos palabras por glosario asignado a su equipo.

## Normas de Contribución y Control de Cambios

- Prohibido tocar o realizar modificaciones sobre la rama `main`.
- Cada equipo debe trabajar estrictamente sobre la rama correspondiente según el glosario asignado (`feature/glosario-ser`, `feature/glosario-software` o `feature/glosario-ingles`). Está prohibido crear ramas adicionales o trabajar sobre las ramas de otros equipos.
- No modificar archivos base ni archivos pertenecientes a otros equipos.
- Verificar previamente que los términos a agregar no se encuentren ya registrados en el glosario.
- Realizar un único commit por persona; ambos términos correspondientes deben incluirse dentro del mismo commit.
> **Recomendacion de commits:** feat(equipo-x):nombre_apellido/materia
