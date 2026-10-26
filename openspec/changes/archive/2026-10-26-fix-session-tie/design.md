# Design

## Decisions

- En `inferSession` el candidato es el de mayor coincidencia; si hay empate con la sesión planificada del día (`sessionFor`), gana la planificada. Sin sesión planificada ese día, el comportamiento no cambia.
- No se toca la elección manual ni el cálculo de coincidencia.

## Risks / Trade-offs

- Si alguien hace de verdad otra sesión con ejercicios compartidos, la app mostrará la planificada hasta que registre algo que la diferencie o la elija a mano. Es el mismo criterio que ya aplica a los empates.
