# Cuantificación de la estrategia: WACC y EVA con datos públicos colombianos

**Camino local en pesos y camino en dólares con riesgo país**

Gerencia Estratégica 2027-1 · Ingeniería Financiera · Universidad de Medellín · Material académico del docente del curso · Versión 1 (noviembre de 2026)

Esta guía acompaña la clase 26 y el punto 3 del P3. Se usa con la plantilla `Clase 26 - WACC, EVA y ROIC.xlsx`.

---

## 1. Para qué sirve

El P3 pide cuantificar la estrategia: el WACC de la empresa por uno de los dos caminos de esta guía, el EVA y el ROIC de los últimos tres años, el efecto esperado de la estrategia sobre el EVA y una sensibilidad (el otro camino y ±1 punto en la prima de mercado). Se entrega en un anexo de una página y en una hoja de cálculo con las fórmulas visibles.

La pregunta de fondo es estratégica, no contable: **¿la empresa gana más de lo que le cuesta el capital que usa, y la estrategia propuesta amplía o reduce esa diferencia?** Las utilidades que superan el costo de capital son rentas económicas, y en una industria competitiva solo se sostienen si la empresa tiene una ventaja que los rivales no pueden imitar fácilmente (Brealey et al., 2010, pp. 308–309). Es el puente entre las cinco fuerzas y el VRIO de la primera parte del curso y las cifras de esta unidad.

---

## 2. Las piezas

| Concepto | Fórmula | Qué dice |
|---|---|---|
| **NOPAT** (utilidad operacional después de impuestos) | EBIT × (1 − t) | Lo que gana la operación, como si no tuviera deuda |
| **Capital invertido** | Deuda financiera + patrimonio total − efectivo | El capital que los inversionistas tienen puesto en la operación |
| **ROIC** | NOPAT / capital invertido | El rendimiento de ese capital |
| **WACC** | E/V × Ke + D/V × Kd × (1 − t) | Lo mínimo que debe rendir ese capital |
| **EVA** | NOPAT − WACC × capital invertido = (ROIC − WACC) × capital invertido | Cuánto valor crea (o destruye) la empresa en el año |

El EVA es una utilidad residual: la utilidad después de cobrar el costo de todo el capital, no solo el de la deuda. Una empresa con utilidad contable positiva puede tener EVA negativo (Brealey et al., 2010, p. 335). La versión de McKinsey, la «ganancia económica», es la misma idea escrita como (ROIC − WACC) × capital invertido (p. 336).

Use la misma unidad en todo (por ejemplo, miles de millones de pesos) y los mismos tres años en todas las filas.

---

## 3. El costo del patrimonio (Ke) y la beta

El curso usa el modelo de valoración de activos de capital (CAPM):

> Ke = tasa libre de riesgo + β × prima de riesgo de mercado

**La beta.** Se estima con una regresión de los rendimientos de la acción contra los rendimientos del índice de mercado, el MSCI COLCAP; es la misma función `PENDIENTE()` del laboratorio de la clase 18. Tres cuidados:

1. **Rendimientos, no precios.** La regresión se hace entre cambios porcentuales, nunca entre niveles de precio e índice, que dan resultados absurdos (Brealey et al., 2010, p. 244).
2. **Suficientes datos.** Use rendimientos mensuales de tres a cinco años o semanales de dos años, y reporte el periodo.
3. **Ruido.** La beta de una sola acción tiene mucho error de estimación; la beta de un grupo de empresas parecidas es más confiable (p. 244). Compare la beta de su empresa con la de la empresa par del sector y, si son muy distintas, explique por qué o use el promedio.

**La prima de mercado.** Es lo que los inversionistas exigen por invertir en acciones en lugar de bonos del gobierno. Fuente del curso: la encuesta anual de Pablo Fernández sobre la prima de mercado y la tasa libre de riesgo que usan profesores, analistas y empresas en cada país (edición 2026, 97 países, en SSRN). Use el valor de Colombia en el camino A y el de Estados Unidos en el camino B.

**Coherencia entre tasa y prima.** Si la tasa libre de riesgo es la de un bono de largo plazo, la prima debe medirse frente a ese mismo tipo de bono (Brealey et al., 2010, p. 245). Por eso el curso usa bonos a 10 años en los dos caminos.

---

## 4. Camino A: en pesos

> **Ke (pesos) = tasa de los TES a 10 años + β × prima de mercado de Colombia**

| Dato | Fuente | Cómo se toma |
|---|---|---|
| Tasa de los TES a 10 años | Banco de la República, curva cero cupón de los TES | El dato más reciente, con fecha |
| Prima de mercado de Colombia | Encuesta de Fernández (valor de Colombia) | Reporte el valor y el año de la encuesta |
| Beta | Regresión contra el MSCI COLCAP | Ver sección 3 |

**El camino A no suma el EMBI.** La tasa de los TES ya es la tasa del gobierno colombiano en pesos: ya incluye el riesgo país y la inflación esperada en Colombia. Sumarle el EMBI sería contar dos veces el riesgo país. Brealey et al. advierten, en general, contra agregar «factores adicionales» a la tasa de descuento para cubrir lo que podría salir mal; recomiendan reflejar esos riesgos en los flujos de caja esperados (2010, p. 247).

---

## 5. Camino B: en dólares con riesgo país

> **Ke (dólares) = tasa del Tesoro de EE. UU. a 10 años + β × prima de mercado de EE. UU. + EMBI de Colombia**
>
> **Ke (pesos) = (1 + Ke en dólares) × (1 + inflación esperada de Colombia) / (1 + inflación esperada de EE. UU.) − 1**

| Dato | Fuente | Cómo se toma |
|---|---|---|
| Tasa del Tesoro a 10 años | FRED (serie DGS10) | El dato más reciente, con fecha |
| Prima de mercado de EE. UU. | Encuesta de Fernández (valor de EE. UU.) | Reporte el valor y el año |
| EMBI de Colombia | J.P. Morgan, vía Boletín Extraoficial | En puntos básicos; 250 puntos son 2,5 % |
| Inflación esperada de EE. UU. | FRED (serie T10YIE, inflación implícita a 10 años) | El dato más reciente |
| Inflación esperada de Colombia | Banco de la República (meta de largo plazo del 3 % o encuesta de expectativas de analistas) | Diga cuál usó |

**Por qué se suma el EMBI aquí.** El Tesoro de EE. UU. no tiene el riesgo de invertir en Colombia; el EMBI mide cuánto más pagan los bonos del gobierno colombiano en dólares que los del Tesoro. Es una práctica muy usada entre analistas, con la objeción de la sección 4: es un factor añadido a la tasa.

**Por qué se convierte a pesos.** Las tasas en monedas distintas no se comparan directamente, como no se compara la altura de un conejo en pulgadas con la de un elefante en pies (Brealey et al., 2010, p. 257). Como los estados financieros están en pesos, el Ke también debe estarlo. La conversión con el diferencial de inflación mantiene la misma tasa real en las dos monedas.

**Por qué los dos caminos dan cifras distintas.** Parten de tasas libres de riesgo distintas (TES frente a Tesoro más EMBI), de primas distintas (Colombia frente a EE. UU.) y de supuestos de inflación. Ninguno es «el correcto»: el P3 pide justificar el elegido y mostrar el otro en la sensibilidad. Si la diferencia es grande, dígalo y explique de dónde viene.

---

## 6. El costo de la deuda, los impuestos y los pesos

**Costo de la deuda (Kd).** Es la tasa que la empresa pagaría hoy por endeudarse, no la tasa pactada cuando emitió la deuda ni el cupón (Brealey et al., 2010, p. 531). Si la empresa tiene bonos que se negocian en la BVC, use su rendimiento actual. Si no, una aproximación es el gasto de intereses del último año dividido por la deuda financiera promedio; dígalo como aproximación.

**Tasa de impuestos (t).** La tarifa general del impuesto de renta en Colombia es 35 %. Algunas actividades, como las entidades financieras, tienen sobretasas temporales; verifiquen la tasa que aplica a su empresa en la nota de impuestos de los estados financieros y citen la página.

**Pesos de deuda y patrimonio.** Use el **valor de mercado del patrimonio**: precio de la acción en la BVC × número de acciones. No use el patrimonio en libros para los pesos (Brealey et al., 2010, p. 531). Para la deuda se acepta el valor en libros de la deuda financiera si la empresa es sana (p. 540). Incluya la deuda de corto plazo si es una fuente permanente de financiación (pp. 539–540).

**Un error común.** El WACC es el de la empresa tal como está financiada, no el de un proyecto que «se financiará con más deuda». Bajar el WACC suponiendo más deuda solo para que el proyecto luzca mejor es el error del «gerente Q» (Brealey et al., 2010, p. 541).

---

## 7. EVA y ROIC de los últimos tres años

Con los estados financieros consolidados de los tres últimos años (Supersociedades, BVC o la página de inversionistas, con página):

1. **NOPAT** = utilidad operacional × (1 − t).
2. **Capital invertido** = deuda financiera de corto y largo plazo + patrimonio total (incluida la participación no controladora) − efectivo y equivalentes. Use el cierre de cada año o el promedio, pero lo mismo en los tres años.
3. **ROIC** = NOPAT / capital invertido.
4. **EVA** = NOPAT − WACC × capital invertido. La plantilla usa el WACC actual para los tres años; es una simplificación que el anexo debe mencionar.

**Cómo leerlo.** El signo del diferencial ROIC − WACC dice si la empresa crea o destruye valor; el tamaño del capital dice cuánto. Una empresa grande con un diferencial pequeño puede crear más valor que una pequeña con un diferencial grande (Brealey et al., 2010, p. 336).

---

## 8. La trampa del crecimiento

Cualquier inversión con rendimiento positivo, aunque sea de 1 % o 2 %, aumenta las utilidades. Si a los gerentes se les pide hacer crecer las utilidades, pueden invertir en proyectos que las aumentan y al mismo tiempo destruyen valor (Brealey et al., 2010, p. 334). Del mismo modo, una empresa que reinvierte sus utilidades a una tasa menor que su costo de capital aumenta sus utilidades a costa del valor de la acción (p. 99).

Con la fórmula del EVA se ve de inmediato: si el capital nuevo rinde lo mismo que el existente,

> Cambio en el EVA = (ROIC − WACC) × capital nuevo

Si el diferencial es negativo, crecer empeora el EVA. **Antes de crecer, hay que mejorar el diferencial.** Es la conexión con las alternativas de crecimiento (clase 17) y de fusiones y adquisiciones (clase 18): una adquisición que aumenta los ingresos pero rinde menos que el WACC es crecimiento que destruye valor.

---

## 9. El efecto de la estrategia sobre el EVA

Para la alternativa elegida en el P2 y desarrollada en el P3, estime en régimen (un año típico, ya implementada):

> Cambio en el EVA = cambio en el NOPAT − WACC × cambio en el capital invertido

- **Cambio en el NOPAT:** el cambio esperado en la utilidad operacional × (1 − t), con el supuesto que lo justifica y su fuente.
- **Cambio en el capital invertido:** la inversión que exige la estrategia.
- **ROIC de la estrategia:** cambio en el NOPAT / cambio en el capital. Si es menor que el WACC, la estrategia cae en la trampa del crecimiento.

Los supuestos son estimaciones; lo que se evalúa es que sean explícitos, tengan fuente y sean coherentes con el BSC de la clase 25.

---

## 10. Bancos y SURA: EVA sobre el patrimonio

En un banco, los depósitos no son una fuente de financiación como la deuda de una empresa industrial: son la materia prima del negocio. Por eso el WACC y el capital invertido no tienen sentido para un banco, y lo mismo ocurre con un holding cuyas filiales principales son financieras y aseguradoras, como SURA. Los equipos de Cibest, Davivienda y SURA usan:

> **Ke** por el camino A o B (secciones 4 y 5)
>
> **EVA sobre el patrimonio** = utilidad neta atribuible − Ke × patrimonio atribuible = (ROE − Ke) × patrimonio

El efecto de la estrategia se calcula igual, con el cambio esperado en la utilidad neta y en el patrimonio. La plantilla trae la hoja «Patrimonio» para estos casos.

**Holdings no financieros (Argos).** Se usa el WACC de los estados consolidados, con una advertencia: un WACC único para negocios muy distintos (cemento, energía, concesiones) puede no servir para ninguno de ellos en particular (Brealey et al., 2010, p. 540). Si la estrategia se concentra en un negocio, dígalo en el anexo.

---

## 11. La sensibilidad

El P3 pide dos ejercicios:

1. **El otro camino:** recalcule el Ke, el WACC y el EVA con el camino que no eligió.
2. **±1 punto en la prima de mercado:** sume y reste un punto a la prima del camino elegido. El Ke se mueve β puntos.

La plantilla los calcula en la hoja «Sensibilidad». **La pregunta clave:** ¿el EVA cambia de signo entre los casos? Si cambia, la conclusión «crea valor» o «destruye valor» depende de los supuestos, y el anexo debe decirlo.

---

## 12. El anexo de una página

1. Camino elegido y por qué, en dos líneas.
2. Tabla de datos con valor, fuente y fecha (o página).
3. Ke, WACC (o Ke para bancos y SURA).
4. Tabla de tres años: NOPAT, capital invertido, ROIC, WACC, diferencial y EVA (o utilidad neta, patrimonio, ROE, Ke y EVA sobre el patrimonio).
5. Efecto esperado de la estrategia sobre el EVA, con sus supuestos.
6. Sensibilidad: el otro camino y ±1 punto en la prima.
7. Lectura estratégica en tres líneas: ¿la empresa crea valor?, ¿la estrategia lo aumenta?, ¿la conclusión resiste la sensibilidad?

---

## 13. Errores que restan puntos

- **Mezclar monedas:** sumar el EMBI a la tasa de los TES, usar la prima de EE. UU. con los TES o dejar el Ke del camino B en dólares.
- **Usar el patrimonio en libros** para los pesos del WACC.
- **Usar la tasa cupón** de la deuda en lugar de la tasa actual.
- **Estimar la beta con precios** en lugar de rendimientos.
- **Cifras sin fuente o tomadas de la IA:** toda cifra sale de una fuente verificable, con fecha o página.
- **Calcular el WACC de un banco** como si fuera una empresa industrial.

---

## Fuentes de datos

| Dato | Fuente | Camino |
|---|---|---|
| Tasa de los TES | Banco de la República, curva cero cupón: https://banrep.gov.co/es/curva-spot-cero-cupon | A |
| Inflación, tasas de colocación | Banco de la República: https://www.banrep.gov.co | A y B |
| Precios de acciones, MSCI COLCAP, bonos | Bolsa de Valores de Colombia: https://www.bvc.com.co | A y B |
| EMBI de Colombia | J.P. Morgan, vía Boletín Extraoficial: https://boletinextraoficial.com/kpi/embi/ | B |
| Tesoro de EE. UU. e inflación implícita | FRED, series DGS10 y T10YIE: https://fred.stlouisfed.org/series/DGS10 | B |
| Prima de mercado | Fernández et al. (2026), encuesta en SSRN | A y B |
| Estados financieros | Supersociedades (datos abiertos), BVC, página de inversionistas | — |

## Referencias

Brealey, R. A., Myers, S. C., & Allen, F. (2010). *Principios de finanzas corporativas* (9.ª ed.). McGraw-Hill.

Fernandez, P., Habibian, A., & Fernández Acín, A. (2026). *Survey: Market risk premium and risk-free rate used for 97 countries in 2026* [Documento de trabajo]. SSRN. https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6570342
