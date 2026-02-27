# Instalación y configuración del simulador y dependencias
## Introducción
En este documento se explica cómo preparar el entorno necesario para ejecutar el proyecto **Pilla-Pilla de Robots**, que consiste en dos agentes (depredador y presa) que aprenden estrategias mediante **aprendizaje por refuerzo**.  

Aquí se detallan los pasos para:

- Configurar el simulador y el entorno de ejecución.
- Instalar las dependencias necesarias (Python, librerías, etc.).
- Usar **Docker** para tener un entorno reproducible sin conflictos de versiones.
- Verificar que el simulador y los agentes funcionan correctamente.

El objetivo es que cualquier persona pueda reproducir los experimentos y pruebas sin problemas, independientemente de su sistema operativo. Comprobar que el simulador funciona correctamente.

## Requisitos previos
## Clonar repositorio
## Configuración del entorno
Existen dos formas de preparar el entorno para ejecutar el simulador y los agentes:
### Con Docker 
El uso de Docker es el más recomendado debido a que permite crear un contenedor con todo el software necesario ya configurado, evitando conflictos de versiones.
Pasos a seguir:
  1. **Construir la imagen:**

```bash
docker build -t refuerzo_multiagente .
```
  2. **Ejecutar el contenedor:**
```bash
docker run -it --rm refuerzo_multiagente
```
  3. **(Opcional) Mapear carpetas para acceder al código desde fuera del contenedor:**
```bash
docker run -it --rm -v $(pwd)/software:/app/software refuerzo_multiagente
```

### Con entorno virtual (venv)
Si prefieres instalar todo directamente en tu máquina, es recomendable usar un entorno virtual para no afectar otras instalaciones de Python.
Pasos a seguir:
  1. **Crear un entorno virtual:**

```bash
python -m venv venv
```
  2. **Activar el entorno:**
```bash
# Linux / Mac
source venv/bin/activate

# Windows
venv\Scripts\activate
```
  3. **Instalar las dependencias:**
```bash
pip install -r requirements.txt
```
  4. **Verificar la instalación ejecutando el simulador:**
```bash
python software/environment.py
```
## Instalación manual de dependencias
## Verificación de instalación
