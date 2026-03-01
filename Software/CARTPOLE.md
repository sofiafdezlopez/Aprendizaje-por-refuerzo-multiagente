# ¿Qué es Cartpole?
Es un entorno clásico de aprendizaje por refuerzo, es considerado un entorno sencillo y estándar para aprender como funcionan los algoritmos de refuerzo debido a que es fácil de simular y visualizar.

Su objetivo es:
  - Muestra/crea un carrito que puede moverse la izquieda o a la derecha sobre una pista
  - Encima del carrito hay un palo vertical (un péndulo invertido)
  - EL objetivo es que el palo vertical este en equilibrio todo el tiempo, evitando que caiga la derecha o a la izquierda.

# ¿Por qué es el primer entorno a utilizar?
- Se podría comparar con un "Hello world", es decir, primeros pasos en el ámbito de refuerzos.
- Permite probar algoritmos sin tener que complicarse con entornos 3D o robots reales.
- Ayuda a entnder como funciona el método de refuerzo entre un agente y la recompensa.

# ¿Qué es lo que he hecho con Cartpole?
```bash
import gymnasum as gym
import time
env = gym.make("CartPole-v1")

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
