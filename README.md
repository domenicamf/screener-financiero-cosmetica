# Screener financiero de la industria de cosmética y maquillaje

Análisis financiero comparativo de cinco empresas de cosmética que cotizan en bolsa, con foco en
**L'Oréal**. El proyecto construye un *screener* que mide rentabilidad, eficiencia, solvencia y
calidad de las utilidades, y termina en un ranking con recomendación de inversión y un dashboard
interactivo.

> Proyecto del curso **Finanzas Computacionales** · Magíster en Business Analytics (UAI), 2026.

---

## Pregunta de negocio

En un período en que la industria de la belleza se deterioró (tres de las cinco empresas
analizadas registraron pérdidas en 2025), **¿qué empresa es la más sólida y cuáles presentan
señales de riesgo?**

## Empresas analizadas

| Empresa | Ticker | Marcas de maquillaje | Norma contable |
|---|---|---|---|
| **L'Oréal** (foco) | `OR.PA` | Maybelline, NYX, Lancôme, Urban Decay | IFRS |
| Estée Lauder | `EL` | MAC, Clinique, Too Faced, Bobbi Brown | US GAAP |
| Coty | `COTY` | CoverGirl, Max Factor, Rimmel | US GAAP |
| Shiseido | `4911.T` | Shiseido, NARS, Clé de Peau | IFRS |
| e.l.f. Beauty | `ELF` | e.l.f., Rhode | US GAAP |

## Principales hallazgos

- **L'Oréal es la empresa más sólida del grupo.** Mantuvo un margen operacional cercano a 20%
  mientras la mediana de sus pares caía de ~11% a −2%. Tiene el ROE más alto (17,5%), sustentado
  en el negocio y no en el endeudamiento, y no presenta señales de alerta en todo el período.
- **Su ventaja no está en fabricar más barato, sino en vender de forma más eficiente:** gasta 51%
  de sus ventas en venta, marketing y administración, el nivel más bajo del grupo.
- **e.l.f. Beauty es la alternativa de crecimiento:** triplicó sus ventas en tres años y empata con
  L'Oréal en el ranking, pero su solidez financiera se debilita en 2026 tras adquirir Rhode.
- **Coty presenta riesgo de insolvencia** (Altman Z'' en zona de quiebra y empeorando cada año).
  Estée Lauder y Shiseido quedan en observación.

## Metodología

1. **Datos:** estados financieros anuales desde `yfinance`, guardados en Parquet con fecha de
   descarga, más un control de calidad (identidad del balance y cobertura de partidas).
2. **Ratios** de liquidez, rentabilidad, endeudamiento y eficiencia.
3. **Análisis DuPont** de tres y cinco factores, motores operacionales y **atribución logarítmica**
   del cambio del ROE.
4. **Common-size** (análisis vertical) y **tendencias** (índice base 100, CAGR).
5. **Peer screening:** percentiles, z-scores, puntaje ponderado y sensibilidad a los pesos.
6. **Señales de alerta:** accruals, **Beneish M-Score** (manipulación de utilidades) y
   **Altman Z''** (riesgo de insolvencia), resumidas en un tablero tipo semáforo.
7. **Dashboard interactivo** en Streamlit.

## Cómo ejecutarlo

**En Google Colab (recomendado):** abrir `Taller_1.ipynb` en Colab y ejecutar todas las celdas
(*Entorno de ejecución → Ejecutar todo*). La sección 11 genera un enlace temporal al dashboard.

**En un computador local:**

```bash
pip install -r requirements.txt
jupyter notebook Taller_1.ipynb
# después de ejecutar el notebook, para abrir el dashboard:
streamlit run app_dashboard.py
```

## Estructura del repositorio

| Archivo | Contenido |
|---|---|
| `Taller_1.ipynb` | Análisis completo, con tablas, gráficos e interpretaciones |
| `requirements.txt` | Librerías necesarias |
| `README.md` | Este resumen |

## Limitaciones

- `yfinance` no es una fuente oficial; las cifras pueden variar levemente según la fecha de descarga.
- Las empresas difieren en norma contable, moneda y cierre fiscal; se usan ratios y un año de
  comparación común (2025) para mitigarlo.
- Beneish y Altman son señales para priorizar la revisión, no pruebas de manipulación o quiebra.

## Herramientas

Python · pandas · NumPy · Matplotlib · yfinance · Plotly · Streamlit

---

**Autora:** Doménica Mercado Fernández · [github.com/domenicamf](https://github.com/domenicamf)
