# Práctica 6 – Modelado de problemas aplicados a la Ingeniería Civil  
### Proyecto: Planificador de Reforestación

---

## 👷‍♂️ Autor
**Alicia Gisel Canche Chan**  
Matrícula: al078755

Asignatura: Modelado de Problemas Aplicados a la Ingeniería Civil  
Docente: Juan Antonio Chuc Méndez

---

## 🎯 Objetivo
Desarrollar un modelo computacional que permita **planificar una reforestación** considerando parámetros técnicos de ingeniería civil y ambiental, como:
- Área disponible para plantación
- Distancia mínima entre árboles
- Tipo de suelo y su efecto en la supervivencia
- Supervivencia esperada por especie
- Costo unitario por árbol
- CO₂ compensado por árbol y total estimado

El sistema calcula automáticamente cuántos árboles plantar, cuántos adicionales para compensar mortalidad, el costo total del proyecto y la captura estimada de CO₂ anual.

---

## 🧮 Modelo matemático

Se basa en las siguientes ecuaciones:

1. **Capacidad teórica de plantación**
   \[
   \text{Capacidad} = \left\lfloor \frac{Área}{(Distancia)^2} \right\rfloor
   \]

2. **Supervivencia efectiva**
   \[
   S_{ef} = S_{usuario} \times M_{suelo}
   \]
   Donde \( M_{suelo} \) es el modificador según tipo de suelo:
   | Tipo de suelo | Modificador |
   |----------------|--------------|
   | Franco (loam)  | 1.00 |
   | Arenoso        | 0.90 |
   | Arcilloso      | 0.95 |
   | Rocoso         | 0.80 |

3. **Árboles a plantar**
   \[
   N_{plantar} = \left\lceil \frac{\text{Capacidad}}{S_{ef}} \right\rceil
   \]

4. **Árboles extra**
   \[
   N_{extra} = N_{plantar} - \text{Capacidad}
   \]

5. **Costo total**
   \[
   C_{total} = N_{plantar} \times C_{unitario}
   \]

6. **CO₂ anual estimado**
   \[
   CO₂_{anual} = N_{plantar} \times S_{ef} \times CO₂_{unitario}
   \]

---

## 🖥️ Interfaz gráfica (GUI)
El programa usa **Tkinter**, permitiendo ingresar los datos mediante una interfaz amigable:

- Entrada de área disponible (m²)
- Distancia mínima entre árboles (m)
- Supervivencia esperada (%)
- Selección de tipo de suelo
- Selección de especie (Pino, Encino, Acacia, Mango)
- Botón **“Calcular plan”**  
- Resultados mostrados en un cuadro de texto: capacidad, árboles extra, costo y CO₂ estimado.

---

## 🧩 Estructura del proyecto

