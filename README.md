# Proyecto-EL4106
Proyecto-EL4106 Este consiste en la implementacion de algoritmos geneticos para el calculo de la cinematica inversa de un brazo robotico de 4dof.

# Links
[Repo brazo 4dof](https://github.com/JavierUR/SimpleArm)


# Meeting 1

## Brazo
<img src="doc/Diagrama_brazo.png" width="800" height="540" />

## Algoritmo Evolutivo
### Definiciones
#### Codificación
Nuestra codificación para cada individuo sigue las normas de evolucion diferencial, en la cual no se consideran un genoma binario si no un genoma de valor Real, basados en el paper xxx es tomar los indivuos como:

<a href="https://www.codecogs.com/eqnedit.php?latex=X=(\theta_1,\theta_2,\theta_3,\theta_4)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?X=(\theta_1,\theta_2,\theta_3,\theta_4)" title="X=(\theta_1,\theta_2,\theta_3,\theta_4)" /></a>
Con cada uno de los angulos los angulos de rotación de cada uno de los motores del brazo. 

Esta solución es la más encontrada en la literatura sobre estos tipos.

Nosotros tambien proponemos la siguente codificacion:

<a href="https://www.codecogs.com/eqnedit.php?latex=X=(\widehat{\theta_1}|\widehat{\theta_2}|\widehat{\theta_3}|\widehat{\theta_4})" target="_blank"><img src="https://latex.codecogs.com/gif.latex?X=(\widehat{\theta_1}|\widehat{\theta_2}|\widehat{\theta_3}|\widehat{\theta_4})" title="X=(\widehat{\theta_1}|\widehat{\theta_2}|\widehat{\theta_3}|\widehat{\theta_4})" /></a>

Donde theta gorro es 
<a href="https://www.codecogs.com/eqnedit.php?latex=\widehat{\theta_i}=\begin{bmatrix}&space;\theta_{i_1}\\&space;\theta_{i_2}\\&space;...\\&space;\theta_{i_j}\\&space;\theta_{i_N}\\&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\widehat{\theta_i}=\begin{bmatrix}&space;\theta_{i_1}\\&space;\theta_{i_2}\\&space;...\\&space;\theta_{i_j}\\&space;\theta_{i_N}\\&space;\end{bmatrix}" title="\widehat{\theta_i}=\begin{bmatrix} \theta_{i_1}\\ \theta_{i_2}\\ ...\\ \theta_{i_j}\\ \theta_{i_N}\\ \end{bmatrix}" /></a>
El cual es el vector de los N de la trayectoria discretizada.

#### Operador Genetico de selección

Para el operador genetico de selección se propone el one to one tournament el cual consite en evaluar el fitnes de los padres y los hijos individuo a individuo en el cual sobrevie el que obtenga un fitness mayor.

#### Croosover


#### Mutación
Se incluye la lista de posibles mutaciones
<img src="doc/mutations.png" width="800" height="540" />


#### Fitness

## Cinematica Directa
Para la cinematica directa se utilzo la formulacion 'Denavit-hartenberg' En la cual tenemos los valores parametrizados de:

Largo=0.5+0.1 mt

altura=0.1 mt

### Traslación de ejes
<a href="https://www.codecogs.com/eqnedit.php?latex=T_t=\begin{bmatrix}&space;0&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;largo\\&space;0&space;&&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?T_{traslacion}=\begin{bmatrix}&space;0&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;largo\\&space;0&space;&&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}" title="T_t=\begin{bmatrix} 0 & 0 & 0 & 0\\ 0 & 0 & 0 & 0\\ 0 & 0 & 0 & largo\\ 0 & 0 & 0 & 1 \end{bmatrix}" /></a>


### Traslación de base
<a href="https://www.codecogs.com/eqnedit.php?latex=T_t=\begin{bmatrix}&space;0&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;altura\_base\\&space;0&space;&&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?T_{traslacion}=\begin{bmatrix}&space;0&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;altura\_base\\&space;0&space;&&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}" title="T_t=\begin{bmatrix} 0 & 0 & 0 & 0\\ 0 & 0 & 0 & 0\\ 0 & 0 & 0 & altura\_base\\ 0 & 0 & 0 & 1 \end{bmatrix}" /></a>

### Rotacion en eje y (brazos)
<a href="https://www.codecogs.com/eqnedit.php?latex=Rot_y=\begin{bmatrix}&space;Cos(\theta)&space;&&space;0&space;&&space;Sen(\theta)&space;&&space;0\\&space;0&space;&&space;1&space;&&space;0&space;&&space;0\\&space;-Sen(\theta)&space;&&space;0&space;&&space;Cos(\theta)&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;0&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Rot_y=\begin{bmatrix}&space;Cos(\theta)&space;&&space;0&space;&&space;Sen(\theta)&space;&&space;0\\&space;0&space;&&space;1&space;&&space;0&space;&&space;0\\&space;-Sen(\theta)&space;&&space;0&space;&&space;Cos(\theta)&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;0&space;\end{bmatrix}" title="Rot_y=\begin{bmatrix} Cos(\theta) & 0 & Sen(\theta) & 0\\ 0 & 1 & 0 & 0\\ -Sen(\theta) & 0 & Cos(\theta)& 0\\ 0 & 0 & 0 & 0 \end{bmatrix}" /></a>

### Rotacion en eje z (base)
<a href="https://www.codecogs.com/eqnedit.php?latex=Rot_z=\begin{bmatrix}&space;Cos(\theta)&space;&&space;-Sen(\theta)&space;&&space;0&space;&&space;0\\&space;Sen(\theta)&space;&&space;Cos(\theta)&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;1&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;0&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Rot_z=\begin{bmatrix}&space;Cos(\theta)&space;&&space;-Sen(\theta)&space;&&space;0&space;&&space;0\\&space;Sen(\theta)&space;&&space;Cos(\theta)&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;1&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;0&space;\end{bmatrix}" title="Rot_z=\begin{bmatrix} Cos(\theta) & -Sen(\theta) & 0 & 0\\ Sen(\theta) & Cos(\theta) & 0 & 0\\ 0 & 0 & 1& 0\\ 0 & 0 & 0 & 0 \end{bmatrix}" /></a>


### Traslación final
<a href="https://www.codecogs.com/eqnedit.php?latex=^{i-1}T_i=T_{traslacion}(Joint_i)&plus;Rot(\theta_i)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?^{i-1}T_i=T_{traslacion}(Joint_i)&plus;Rot(\theta_i)" title="^{i-1}T_i=T_{traslacion}(Joint_i)+Rot(\theta_i)" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=T_{base}=\prod_{i=1}^{n}^{i-1}T_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?T_{base}=\prod_{i=1}^{n}^{i-1}T_i" title="T_{base}=\prod_{i=1}^{n}^{i-1}T_i" /></a>
