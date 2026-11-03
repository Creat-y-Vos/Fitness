## Decisiones
- **`stack` opcional y ordenado** en el ejercicio; sin `stack` todo funciona como antes con `step`.
- **Siguiente/anterior por comparación con tolerancia (0,01)**: si la carga actual no está en la lista (tipeada a mano), "+" va a la próxima mayor y "−" a la próxima menor; por debajo de la primera, "−" llega a 0.
- **Tipear sigue permitido**: la lista guía los botones, no limita el campo.
- **Sugerencia**: `ref × factor` se redondea al valor más cercano de `stack`.
- El config sigue siendo del servidor (solo lectura desde la app); `stack` se agrega por SQL.

## Riesgos
- Un `stack` mal cargado desordena los saltos: se ordena al leer.
- Cada máquina del gimnasio tiene su pila; solo se cargó la de bíceps de la foto.
