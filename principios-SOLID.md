```properties
PRINCIPIOS SOLID
: Los principios de diseño S.O.L.I.D son una serie de normas o recomendaciones que guian un poco la forma de diseñar nuestros sistemas.

S.O.L.I.D hace referencia a cinco(5) principios
: ( Los cuales fueron impulsados por Robert C.Martin, aunque el nombre de SOLID lo puso Michael Feathers)
```

```scss
// QUE SE BUSCA CON SOLID ?

- Código mas Mantenible.
- Un código Fácil de cambiar.
- Muy extensible
```

```scss
S => "Single Responsibility Principle" (Principio de responsabilidad única)
O => "Open Closed Principle" (Principio Abierto Cerrado)
L => "Liskov Substitution Principle" (Principio de sustitución de Liskov)
I => "Interface Segregation Principle" (Principio de segregación de interface)
D => "Dependency Inversion Principle" (Principio de inversión de la dependencia)
```

```properties
---------------------------------------------------------------------------
S -> Single Responsibility Principle - Principio de Responsabilidada Única
---------------------------------------------------------------------------
```

```scss
"Cada CLASE debería tener una sola responsabilidad", debería encargarse de una sola parte del sistema. "El objetivo es conseguir que nuestras clases hagan una sola cosa". De esta forma podemos asegurarnos que la hace muy bien.

"Ejemplo" 
Registro de un nuevo usuario en una plataforma web.

(Podríamos tener en la lógica de creación del usuario, el encriptado de su contraseña, pero si lo hicieramos así le estamos dando a esta clase "dos responsabilidades" aunque parezca que no. Una responsabilidad es crear el propio objeto del Usuario con la información necesaria que define esta clase. Otra decidir como encriptar su contraseña. "POR LO TANTO ESTAMOS ROMPIENDO EL PRINCIPIO DE RESPONSABILIDAD UNICA") 

// Deberiamos modificar esta clase si queremos adicionarle atributos al usuario, tanto si queremos cambiar nuestro algoritmo de encriptación. COSA QUE NO TIENE NINGUN SENTIDO, ya que el ALGORITMO DE ENCRIPCIÓN SE DEBERÍA CAMBIAR EN UN SOLO LUGAR Y NO EN VARIAS CLASES.

```

<img src="images\image-20210125143347879.png" alt="image-20210125143347879" style="zoom:150%;" />

```scss
La forma correcta de hacerlo según RPC, sería "mover todo el código de encriptación a su propia clase". Para que de esta forma el comportamiento quede "ENCAPSULADO" 

// (Facilitando el cambio del algoritmo de encripción en el futuro, en un solo lugar)
```

![image-20210115181525325](images\image-20210115181525325.png)

![image-20210115181543965](images\image-20210115181543965.png)

```scss
// La clase Usuario (UserRegistry) DELEGA a la clase de Encriptado (PasswordEncrypter) la responsabilidad que ella no puede asumir.
```

```properties
------------------------------------------------------
O -> Open Closed Principle - Principio Abierto Cerrado
------------------------------------------------------
```

```scss
"Una entidad de Software" debe quedarse "ABIERTA para su extensión (HERENCIA)" pero "CERRADA para su modificación". Lo que logramos con este principio es que la funcionalidad basica de nuestro sistema este protegida (Que no se pueda romper). 

// Las herramientas que nos facilitan esta tarea son la HERENCIA y el POLIMORFISMO

"Ejemplo:" 
Supongamos que tenemos un clase que define rectangulos
```

![image-20210115182448774](images\image-20210115182448774.png)

![image-20210115182604372](images\image-20210115182604372.png)

```scss
Esto funciona perfectamente, pero que pase si queremos que calcule areas de triangulos ????
// TENDRIAMOS QUE MODIFCIAR NUESTRA CLASE PARA TENER EN CUENTA EL AREA DEL TRIANGULO ?????
```

![image-20210115182830178](images\image-20210115182830178.png)

```scss
Y esto nos pasara cada vez que querramos añadir funcionalidades. "Nuestra clase esta abierta para su MODIFICACION por lo que no estamos cumpliendo el segundo principio SOLID". Por lo que hay peligro de agregar bugs cada vez que querremos añadir nueva funcionalidad. "La forma correcta de hacerlo sería utiliza POLIMORFISMO en este caso"
```

![image-20210115183141654](images\image-20210115183141654.png)

![image-20210115183402093](images\image-20210115183402093.png)

```scss
"El anterior es un modelo mas ROBUSTO y MAS FACIL de extender."
```

```properties
-----------------------------------------------------------------------
L -> Liskov Substitution Principle - Principio de sustitución de Liskov
-----------------------------------------------------------------------
```


```scss
Basicamente lo que nos dice este principio es que "toda clase que es hija de otra clase", debe poder utilizarse como si fuera el mismo padre.

// Un Pato de Goma Nada, Hace cuack pero no Vuela. Si devolvemos ERROR al volar ESTAMOS VIOLANDO EL PRINCIPIO DE SUSTITUCIÓN. Ya que el sistema se comportara diferente si estamos frente a un pato de goma o ante un pato convencional
```

![image-20210115183924836](images\image-20210115183924836.png)

![image-20210115184230919](images\image-20210115184230919.png)

```scss
"SOLUCION CORRECTA SIN VIOLAR EL PRINCIPIO 3" 

// Crear interfaces para Volar, Nadar y Hacer cuack.
De esta manera cada tipo de pato implementa las operaciones que necesite.
```

![image-20210115184335775](images\image-20210115184335775.png)

![image-20210115184549053](images\image-20210115184549053.png)

```properties
----------------------------------------------------------------------------
I -> Interface Segregation Principle - Principio de segregación de interface
----------------------------------------------------------------------------
```

```scss
-----------------------------------------------------------------------------------------------------
Es mucho mejor tener "muchas clases pequeñas y especializadas" que una "clase enorme con varios métodos".
-----------------------------------------------------------------------------------------------------
```

```properties
------------------------------------------------------------------------------
D -> Dependency Inversion Principle - Principio de inversión de la dependencia
------------------------------------------------------------------------------
```


```scss
"Los MÓDULOS DE ALTO NIVEL" no deberían depender de los "MÓDULOS DE BAJO NIVEL". Ambos deberían depender de interfaces. Este principio se basa en la "ABSTRACCIÓN". Esto nos permite reducir "el DESACOPLE entre SISTEMAS DE SOFTWARE".

// Ejemplo:
"No depender si nuestra Base de Datos" utiliza una "tecnología u otra". Porque nuestro código no depende de ninguna forma de que BD utilizamos. Si no de una abstracción que hemos construido en el medio.
```

![image-20210115185510772](images\image-20210115185510772.png)

![image-20210115185540937](images\image-20210115185540937.png)