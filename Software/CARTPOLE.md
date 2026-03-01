# ¿Qué es CartPole?
Es un entorno clásico de aprendizaje por refuerzo, es considerado un entorno sencillo y estándar para aprender como funcionan los algoritmos de refuerzo debido a que es fácil de simular y visualizar.

Su objetivo es:
  - Muestra/crea un carrito que puede moverse la izquieda o a la derecha sobre una pista
  - Encima del carrito hay un palo vertical (un péndulo invertido)
  - EL objetivo es que el palo vertical este en equilibrio todo el tiempo, evitando que caiga la derecha o a la izquierda.

# ¿Por qué es el primer entorno a utilizar?
- Se podría comparar con un "Hello world", es decir, primeros pasos en el ámbito de refuerzos.
- Permite probar algoritmos sin tener que complicarse con entornos 3D o robots reales.
- Ayuda a entnder como funciona el método de refuerzo entre un agente y la recompensa.

# ¿Qué es lo que he hecho con CartPole?
```bash
import gymnasium as gym
import time
env = gym.make("CartPole-v1", render_mode="human")

state, info = env.reset()
print("Estado inicial:", state)

for step in range(10):
    action = env.action_space.sample()  # acción aleatoria
    state, reward, terminated, truncated, info = env.step(action)

    print("Acción:", action)
    print("Nuevo estado:", state)
    print("Recompensa:", reward)
    time.sleep(1)
    if terminated or truncated:
        print("Episodio terminado")
        state, info = env.reset()

env.close()
```

1. **Creación del entorno**
   ```bash
   env = gym.make("CartPole-v1", render_mode="human")
   ```
   - **gym.make("Cartpole-v1")** crea el entorno que se va a usar.
   - **gym** es un paquete que contiene muchos entornos listos de refuerzo.
   - **"CartPole-v1"** es el entorno que se quiere crear.
   - **render_mode="human"** se encarga de la simulación por pantalla.
   
2. **Reset del entorno**
   ```bash
   state, info = env.reset()
   ```
   - Inicializa el estado inicial, que es generado por el entorno (posición del carrito, ángulo, velocidades)
   - **info** contiende datos extra no necesarios.
   
3. **Elección de acción**
   ```bash
   action = env.action_space.sample()  # acción aleatoria
   ```
   - Decide la acción de manera aleatoria, 0 indica mover a la izquierda y 1 mover a la derecha.
     
4. **Avanzar un paso**
   ```bash
   state, reward, terminated, truncated, info = env.step(action)
   ```
   - **.step(action)** hace todo lo que antes te expliqué:

      1. Aplica la acción al entorno.
      
      2. Actualiza el estado.
      
      3. Devuelve la recompensa automáticamente (+1 si el palo sigue en equilibrio, 0 si se cae).
      
      4. Indica si el episodio terminó (terminated) o se truncó por límite de pasos (truncated).
      
      Aquí no decides la recompensa, Gym lo hace por ti según las reglas del CartPole.
   
5. **Reset si termina**
   ```bash
   if terminated or truncated:
    print("Episodio terminado")
    state, info = env.reset()
   ```
   - Si el palo se cae o se llega al límite de pasos, el entorno se reinicia automáticamente.
   
