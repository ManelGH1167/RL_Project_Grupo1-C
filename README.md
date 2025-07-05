# RL_Proyecto_practico_Grupo1_C
## Proyecto Final de programacion para la asignatura de **Aprendizaje por Refuerzo** del master en IA en la Universidad Interacional de Valencia (VIU)

* Alumno 1: Benali, Abdelilah 
* Alumno 2: Cuesta Cifuentes, Jair 
* Alumno 3: González Huete, Manel
* Alumno 4: Manzanas Mogrovejo, Francisco
* Alumno 5: Pascual Redondo, Guadalupe

> Fecha de entrga : 5-July-2025

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

Se ha de tener presente los siguientes aspectos de configuración que pueden afectar a la ejecución:
- En el punto: 1.4. Instalar librerías necesarias, tener presente el parámetro "INSTALL_LOCAL = False". <br>Si se ha realizado la carga de las librerías necesarias, mediante el fichero "requirements_v2.txt", no es necesario volver a realizar este proceso, se asumen que ya estan cargadas, por lo que se establece este parámetro (False) para que no las vuelva a cargar.

- Los check_point temporales se guardarán en el subdirectorio "checkpoints"

- Los videos resultantes se guardarán en el subdirectorio "checkpoints\videos"

- En "Definición Hiperparámetros" se pueden modificar los parámetros: total_episodios = 100, max_steps = 3000, NUM_TRAINING_STEPS = 2000000 (pasos) y batch_size = 32 <br>--> <b>NOTA:</b> Si se quieren hacer pruebas, pero la ejecución final deberá ser con estos valores, e incluso superiores, si queremos que aprenda y llegue a los 20 puntos

- En el último paso, el "main":
> * Tener presente el parámetro  "training_global = True": (entrenar = si) determina que el modelo se utilizará en modo "entrenamiento", cargará los modelos (configurados), creará el agente, cargará los pesos (si > > existen) y lo entrenará. Si por el contrario no queremos entrenar, porque ya lo tenemos todo y queremos pasar a evaluar el modelo y grabar a video la mejor partida --> se pone a <b>False</b>
> <pre> ```python     
> def main(env):
>     tf.keras.backend.clear_session()
>     # Control global de si se entrena o solo se carga
>     training_global = False
>     :
>      ``` </pre>
> El código subido en la actualidad asume que está todo entrenado y sólo realiza evaluación, por lo que training_global está en False
<br>

> * Se puede parametrizar la lista: modelos_a_procesar <br> Con esto se puede configurar si se quiere ejecutar un modelo u otro<br>
> <pre> ```python     
> # Lista de tuplas (nombre_modelo, clase_modelo, flag_entrenamiento_especifico)
>     modelos_a_procesar = [
>         ('DQN', create_dqn_model, True),
>         ('DDQN', create_ddqn_models, False),    
>         ('DDQN_REPLAY', create_ddqn_replay_model, False),
>         ('DUELING_DQN_REPLAY', create_dueling_dqn_replay_model, False)        
>     ] ``` </pre>
> <b>Por ejemplo:</b>  ('DQN', DQNetwork, True), este registor explicita que se realizará el entrenamiendo de DQN y el resto de modelos no se ejecutarán al estar en False<br>
<br>

> * Hay otros parámetros que afectan al proceso de "justificación" de los resultados, donde se leen ficheros txt con la salida (output) de los diferentes entrenos, que posteriormente se pasan a csv, para su representación gráfica:
> <pre> ```python     
> file_Output = 'output-train-'
> parse_output=False
> to_csv=True
> ```</pre>
> 
> * <b>file_Output:</b> es el nombre por el que comenzarán los ficheros utilizados por los procesos de justificación/graficación. Tras este texto, se concatenará el nombre del modelo procesado (DQN, DDQN, etc)
> 
> * <b>parse_output:</b> este flag controla si se ha de realizar un parseo del fichero texto extraido del output de la ejecución (fichero con mucho contenido y datos intranscendentes). Este parseo convierte el fichero texto a csv, más amigable y fácil de procesar a posteriori. Si se establece a False no se parsea el fichero (y no sobreescribirá los csv existentes), la primera vez que tengamos un "txt" con la salida de una ejecución si que tendremos que ponerlo a True para que lo parsee, pero una vez dispongamos del csv, no será necesario volver a ponerlo a True (a no ser que se disponga de otra salida en txt)
> 
> * <b>to_csv:</b> con este flag, indicamos al proceso que disponemos de un fichero csv (parseado) con datos estadisticos de todas las ejecuciones y que nos permite cargar en un dataframe para posteriormente realizar las gráficas comparativas de los resultados obtenidos según el modelo procesado (DQN, DDQN, etc)


------

### ENTORNO
- Windows 10/11
- Python 3.8
- Conda 25.5.1
