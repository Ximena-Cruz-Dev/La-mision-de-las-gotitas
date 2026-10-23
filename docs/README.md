# La misión de las gotitas 💧

## Descripción del proyecto
La misión de las gotitas es un videojuego educativo diseñado para niños de 5 a 7 años. Su propósito es enseñar, de una manera sencilla, interactiva y divertida, la importancia de cuidar el agua potable y utilizarla responsablemente.

Mediante retos y actividades, el videojuego busca que los niños identifiquen acciones adecuadas para ahorrar agua y comprendan por qué este recurso es fundamental para la vida.

## Objetivo de Desarrollo Sostenible 6 (ODS 6)
El proyecto se relaciona con el ODS 6: Agua limpia y saneamiento, establecido por las Naciones Unidas. Este objetivo busca garantizar la disponibilidad de agua, su gestión sostenible y el saneamiento para todas las personas.

El videojuego contribuye a este propósito desde la educación, fomentando hábitos responsables desde la infancia.

---

## 1. Diagrama de Casos de Uso General

```mermaid
flowchart LR
    N["Niño / Guardián del agua"]

    subgraph S["La misión de las gotitas"]
        A(["Iniciar juego"])
        B(["Conocer la historia"])
        C(["Elegir una misión"])
        D(["Responder preguntas"])
        E(["Ver si la respuesta es correcta"])
        F(["Consultar progreso"])
        G(["Salir del juego"])
    end

    N --- A
    N --- B
    N --- C
    N --- D
    N --- E
    N --- F
    N --- G

    A --> B
    B --> C
    C --> D
    D --> E
    E --> C
```

### Explicación:
Este diagrama muestra la interacción del jugador con el sistema: le permite iniciar el juego, elegir misiones y responder preguntas, mientras el sistema valida las respuestas y calcula su puntuación.

---

## 2. Diagrama de Clases 

```mermaid
classDiagram
    class Mision {
        +String nombre
        +String descripcion
        +mostrarMision()
    }

    class Pregunta {
        +String enunciado
        +mostrarPregunta()
        +verificarRespuesta()
    }

    class OpcionRespuesta {
        +String texto
        +Boolean esCorrecta
    }

    class Jugador {
        +String nombre
        +int puntos
        +responderPregunta()
        +sumarPuntos()
    }

    class Retroalimentacion {
        +String mensaje
        +mostrarMensaje()
    }

    Mision "1" --> "1..*" Pregunta : contiene
    Pregunta "1" --> "2..*" OpcionRespuesta : presenta
    Jugador --> Pregunta : responde
    Pregunta --> Retroalimentacion : genera
```

### Explicación:
Muestra la estructura interna de clases del módulo, definiendo cómo la entidad `Mision` se compone de preguntas que el `Jugador` responde para recibir retroalimentación.
