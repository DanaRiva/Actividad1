# Actividad1

Después de limpiar el entorno, creamos las variables simbólicas para realizar el cálculo de las velocidades, en este caso por ser un robot tipo péndulo se requieren los ángulos 

``` matlab
syms th1(t) a1 th2(t) a2 th3(t) a3 t
```
Se genera la configuración del robot con 0 porque es un movimiento rotacional 

``` matlab
RP=[0 0 0];
```

Se derivan los ángulos con respecto al tiempo para obtener las velocidades lineales 

``` matlab
Qp= diff(Q, t);
``` 

Se realizan los vectores con las funciones para modelar las posiciones y la rotación de cada articualación y por el tipo de movimiento son las mismas para las tres articulaciones, la diferencia es la indexación, que corresponde a la articulación que toca 

``` matlab
P(:,:,1)= [a1*cos(th1);
           a1*sin(th1);
                    0];

R(:,:,1)= [cos(th2) -sin(th2) 0;
           sin(th2)  cos(th2) 0;
           0         0        1];
``` 

Se crean las matrices de transformación locales y globales y el algoritmo para generar las matrices

Luego creamos las derivadas parciales para la amtriz jacobiana para cada una de las articulaciones con respecto a X,Y y Z

``` matlab
Jv11= functionalDerivative(PO(1,1,GDL), th1);
``` 
Finalmente se aplica el algoritmo para realizar el cálculo de las velocidades angulares y lineales regresando estos resultados:

![image](https://user-images.githubusercontent.com/100874942/221391200-c28e2642-213a-43f1-aa3a-557a461ec73d.png)



