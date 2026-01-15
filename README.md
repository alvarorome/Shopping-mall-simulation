# Simulación de un Centro Comercial con Arena Simulation  
**Proyecto FInal de Optimización y Simulación – Universidad Pontificia Comillas (ICAI)**

Este repositorio contiene el modelo, documentación y resultados del proyecto de simulación de eventos discretos desarrollado con **Arena Simulation**, cuyo objetivo es analizar el funcionamiento operativo de un centro comercial compuesto por varios establecimientos: un restaurante, una tienda de ropa y una zapatería.

---

##  Objetivo del Proyecto

El propósito del modelo es **representar y evaluar el flujo de clientes** dentro del centro comercial, considerando:

- Llegadas aleatorias de clientes  
- Asignación de atributos y destinos  
- Procesos de atención con recursos limitados  
- Comportamiento secuencial (primer y segundo destino)  
- Medición de tiempos, colas y utilización de recursos  
- Identificación de cuellos de botella  
- Evaluación de escenarios alternativos  

El modelo permite estudiar el rendimiento del sistema y proponer mejoras operativas basadas en datos.

---

##  Descripción del Modelo

### 1. **Generación de Clientes**
Los clientes se crean mediante un módulo **Create** con una distribución exponencial `EXPO(2)`, generando hasta 600 entidades.

### 2. **Asignación de Atributos**
Cada cliente recibe:
- **Prisa** (30% con prisa, 70% sin prisa)  
- **Destino principal** (restaurante, ropa o zapatos)  
- **Segundo destino** opcional  
- **Contador de visitas** inicializado a 0  

### 3. **Enrutamiento**
Un módulo **Decide** dirige al cliente al establecimiento correspondiente según su atributo de destino.

### 4. **Procesos de Atención**
Cada establecimiento utiliza un módulo **Process (Seize–Delay–Release)** con recursos limitados:

| Establecimiento | Recurso | Tiempo con prisa | Tiempo sin prisa |
|----------------|---------|------------------|------------------|
| Restaurante | Mesas | TRIA(10,15,20) | TRIA(20,35,50) |
| Ropa | Empleados | TRIA(3,6,10) | TRIA(5,10,15) |
| Zapatería | Empleados | TRIA(5,8,12) | TRIA(7,12,18) |

### 5. **Registro de Visitas**
Tras cada proceso, un módulo **Assign** incrementa el contador de visitas y registra estadísticas.

### 6. **Decisión Final**
El módulo **Salida o destino** determina si el cliente:
- Sale del sistema  
- O se dirige a un segundo establecimiento  

### 7. **Salida del Sistema**
Los clientes finalizan su recorrido en un módulo **Dispose**.

---

## Resultados Principales

La primera simulación reveló:

- **Zapatería**: principal cuello de botella, acumulando colas superiores a 20 clientes.  
- **Restaurante**: tiempos de servicio más cortos, colas máximas de 3–4 clientes.  
- **Tienda de ropa**: congestión moderada.  
- **Tiempo total medio en el sistema**: ~1.50 horas.  
- **Utilización de recursos**: empleados de tiendas con alta carga de trabajo.

---

## Mejoras Implementadas

Tras analizar los resultados, se decidió:

- Mantener los tiempos de llegada y servicio (representan bien la realidad).  
- **Incrementar los recursos** en las tiendas:  
  - Empleados de ropa: de 3 → 6  
  - Empleados de zapatería: de 3 → 5  
  - Mesas del restaurante: de 7 → 13  

Esto redujo significativamente las colas y equilibró el sistema sin alterar la dinámica temporal.

---

## Contenido del Repositorio

- Proyecto_simulación.pdf
- README.md
- shopping_mall_inicial.doe
- shopping_mall_inicial_rpt.xlsm

---

## Tecnologías Utilizadas

- **Arena Simulation** (Rockwell Automation)  
- Modelado de eventos discretos  
- Distribuciones estadísticas (EXPO, TRIA, DISC)  
- Análisis de colas y recursos  

---

## Autores

- Javier Mendoza Guerrero  
- Luis Bertrán Vidal Campos  
- Álvaro Rodríguez Mesa  
- Carlos Hernández López  

---
