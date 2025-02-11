# Laboratorio No. 03 - 2024-II - Robótica de Desarrollo, Intro a ROS

## Autores

Johan López - [@ElJoho](https://github.com/ElJoho)

Christian Cuestas - [@ChrisCuestas](https://github.com/ChrisCuestas)

## __1. Instalación de ROS2 en una máquina con OS Windows 11__

Se escogió Miniforge3, una distribución de Conda/Mamba optimizada para usar el canal conda-forge, para instalar ROS 2 de forma sencilla, sin necesidad de usar Docker o WSL en Windows.

### 1.1. Instalación de Miniforge3

1. Descargar el instalador para windows desde [el repositorio oficial de Miniforge3](https://github.com/conda-forge/miniforge?tab=readme-ov-file#windows).

2. Ejecutar el instalador.

3. Dar click en el primer "Next" y leer y aceptar el "License Agreement".

4. En el tipo de instalación, seleccionar "Just me (recommended)" y "Next".

5. Determinar el directorio en donde se van a instalar los paquetes y "Next".

6. Marcar las opciones de 

    - Agregar Miniforge3 al PATH environment variable
    - Registrar Miniforge3 como el Python por defecto 

7. Dar click en instalar y esperar a que se realice la instalación

### 1.2 Creación del canal 

Para la creación del canal, en la terminal de Windows (no PowerShell) se ejecuta el siguiente comando:


```shell
conda install mamba -c conda-forge
```

Después de cerrar la terminal y abrir otra, se podría usar el comando `mamba`. PAra probar que funcione:


```shell
mamba --version
```

### 1.3. Instalación de ROS2 con RoboStack

Abrir la terminal de Miniforge3 y seguir los siguientes pasos:

1. Creación del env:

    ```shell
    mamba create -n ros2_env python=3.11
    ```

    Para confirmar la creación, en listamos los envs:

    ```shell
    mamba env list
    ```
    Si en la columna 'Name' aparece un asterisco hay que solucionarlo así:
    ```shell
    conda config --append envs_dirs C:\Users\Zenbook\miniforge3\Library\envs
    ```
    Como resultado debe aparecer así:
    ```
      Name      Active  Path
    -----------------------------------------------------------------------
      base              C:\Users\Zenbook\.mamba
                        C:\Users\Zenbook\anaconda3
                        C:\Users\Zenbook\anaconda3\envs\pythonProject
                        C:\Users\Zenbook\anaconda3\envs\pytorch
                *       C:\Users\Zenbook\miniforge3
      ros2_env          C:\Users\Zenbook\miniforge3\Library\envs\ros2_env
    ```

2. Activar el env:

    ```shell
    mamba activate ros2_env
    ```

3. Instalar conda en el env:
    ```shell
    mamba install conda -n ros2_env
    ```

4. Agregar el canal conda-forge a la configuración del nuevo env creado:
    ```shell
    conda config --env --add channels conda-forge
    ```

5. Agregar el canal robostack-staging a la configuración del nuevo env creado:
    ```shell
    conda config --env --add channels robostack-staging
    ```

6. Instalar ROS2 Humble en el env:
    ```shell
    mamba install ros-humble-desktop
    ```
    Para probar que todo está bien, se corre:

    ```shell
    rviz2
    ```

7. (Opcional) Instalación de paquetes de desarrollo
    ```shell
    mamba install compilers cmake pkg-config make ninja colcon-common-extensions catkin_tools rosdep
    ```

8. Para salir del env:
    ```shell
    mamba deactivate
    ```

## __2. Instalación de Visual Studio 2022 Community__

1. Descargar el instalador desde le página oficial: https://visualstudio.microsoft.com/es/vs/community/

2. Click en Continuar para aceptar términos de licencia y esperar a que el instalador esté listo.

3. En la pestaña 'Cargas de trabajo' seleccionar la opción "Desarrollo para el escritorio con C++".

4. En el panel derecho aparencen muchas características opcionales, solamente dejar seleccionadas las siguientes:
    - Herramientas de compilación de C++ de M...
    - Herramientas de CMake en C++ para Wind...
    - Windows 11 SDK.

5. Seleccionar la mejor forma de instalación y dar click en "Instalar".

## __3. Toolbox de ROS para MATLAB__

1. Abrir MATLAB e ir a la opción "Get Add-Ons".

2. Buscar el ROS Toolbox y dar click en el botón que de inicio a la instalación.

3. Para comprobar que está correctamente instaldo y funcionando, en la ventana de comandos de MATLAB ejecutar:

    ```MATLAB
    ver('ros')
    ```

    Debería devolver algo como:

    ```
    -----------------------------------------------------------------------------------------------------
    MATLAB Version: 24.2.0.2740171 (R2024b) Update 1
    MATLAB License Number: 40830014
    Operating System: Microsoft Windows 11 Home Version 10.0 (Build 26100)
    Java Version: Java 1.8.0_202-b08 with Oracle Corporation Java HotSpot(TM) 64-Bit Server VM mixed mode
    -----------------------------------------------------------------------------------------------------
    ROS Toolbox                                           Version 24.2        (R2024b)
    ```
