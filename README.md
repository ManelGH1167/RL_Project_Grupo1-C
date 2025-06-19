# RL_Proyecto_practico_Grupo1_C
## Proyecto Final de programacion para la asignatura de **Aprendizaje por Refuerzo** del master en IA en la Universidad Interacional de Valencia (VIU)

* Alumno 1: Benali, Abdelilah 
* Alumno 2: Cuesta Cifuentes, Jair 
* Alumno 3: González Huete, Manel
* Alumno 4: Manzanas Mogrovejo, Francisco
* Alumno 5: Pascual, Guadalupe

> Fecha de entrga : 7-July-2025

-----

### PASOS PARA EJECUTAR EL PROYECTO
1º Instalar .exe de la carpeta */to_install*

2º Crear un entorno en CONDA utilizando las librerias en *requirements.txt*
<br>(Si hay problemas con este fichero se puede hacer una llamada a "install.bat")
<br>
>2.1 Crear entorno nuevo:<br>
>`conda create -n miar_rl python=3.8 -y`<br>
>`conda activate miar_rl`<br>


3º Ejecutar el notebook de Python con este entorno desde el paso 3 (paso 1 y 2 no son necesarios, al menos en local)

> Se ha de tener presente los siguientes aspectos de configuración que pueden afectar a la ejecución:
- En el punto: 1.4. Instalar librerías necesarias, tener presente el parámetro "IN_LOCAL = True". <br>Se presupe que las librerías necesarias ya estan cargadas por lo que se establece este parámetro para que no las vuelva a cargar.

- Ver el punto In[6] de ejecución (# Configurar TensorFlow para CPU) cambiar los valores según las cpus de tu máquina.

- Los check_point temporales se guardarán en el subdirectorio "checkpoints"

- En "Definición Hiperparámetros" se pueden modificar los parámetros: total_episodios = 100, max_steps = 3000 y batch_size = 32 <br>--> *NOTA:* si se quieren hacer pruebas. Pero la ejecución final deberá ser con estos valores, e incluso superiores, si queremos que aprenda y llegue a los 20 puntos

- En el último paso, el "main":
> * El parámetro  "training_global = True": (entrenar = si) si no queremos entrenar, porque ya lo tenemos todo y queremos pasar a ejecutar/probar se pone a False<br><br>
> * Se puede parametrizar la lista: modelos_a_procesar <br> Con esto se puede parametrizar si se quiere ejecutar un modelo u otro<br>
*Por ejemplo:*  ('DQN', DQNetwork, False), el ultimo False dice que el modelo DQN no se carga ni entrena, si se quiere cargar y entrenar, poner a True
 

 (batch)


------

### ENTORNO
- Windows 10/11
- Python 3.8
- Conda 25.5.1