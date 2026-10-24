## ADDED Requirements

### Requirement: Comparación de dominadas por agarre
La nota semanal SHALL comparar dominadas solo entre series del mismo agarre, SHALL usar el agarre prono como referencia de progreso y SHALL mencionar las series de otros agarres como variante sin contarlas como mejora de fuerza.

#### Scenario: Semana con agarre neutro
- **WHEN** el usuario hizo más repeticiones en neutro que su mejor serie en prono
- **THEN** la nota NO afirma que mejoró en dominadas estrictas

#### Scenario: Registros sin agarre
- **WHEN** un registro de dominada no tiene agarre
- **THEN** la nota lo trata como prono
