# PPS-Unidad2Actividad1-Angel

# Trazado de una vulnerabilidad.
Actividad 1 de la Unidad 1 de Puesta en Producción Segura. Tabajaremos con los Entornos de Desarrollo

Tenemos varios objetivos:

> [Conocer las diferentes listas que tienen que ver con amenazas de seguridad.](#Listas)

> [Obtener información de una vulnerabilidad navegando por las webs de los organismos que mantienen esas listas.](#Trazado)

---
## Listas

En el siguiente [enlace](https://moodle.educarex.es/ccff_iesvjp/pluginfile.php/27882/mod_resource/content/17/PresentacionUnidad2NivelesSeguridadAplicaciones2025.pdf) podemos visitar al presentación donde encontramos información acerca de las organizaciones y agencias que mantienen información sobre amenazas, vulnerabilidades, debilidades, etc...


## Trazado
Vamos a seguir el trazado de una vulnerabilidad a partir de [este artículo del INCIBE](https://www.incibe.es/empresas/avisos/autodesk-ha-publicado-multiples-vulnerabilidades-que-afectan-autocad).

En el artículo, nos informan sobre varias vulnerabilidades presentes en la aplicación **AutoCAD**, desarrollada por **Autodesk**.
Cierto es verdad, que no proporcionan información sobre el número específico de la vulnerabilidad, sin embargo, si queremos obtener más detallas, podemos consultar el apartado de **referencias** donde nos indican una referencia del desarrollador.

Accediendo al siguiente artículo [https://www.autodesk.com/trust/security-advisories/adsk-sa-2023-0018](https://www.autodesk.com/trust/security-advisories/adsk-sa-2023-0018) nos muestran la información mencionada anteriormente. 

![image](https://github.com/user-attachments/assets/31cbccd4-621e-4b46-82bb-f7f9172be40e)


## Referencias del Desarrollador

En la sección de referencias, se menciona una referencia del desarrollador que puede ayudarnos a obtener más información sobre las vulnerabilidades identificadas en la aplicación.

___

Dándole al enlace nos lleva a la página: [https://www.autodesk.com/trust/security-advisories/adsk-sa-2023-0018](https://www.autodesk.com/trust/security-advisories/adsk-sa-2023-0018)

## Información sobre Vulnerabilidades
Allí vemos una descripción de los problemas y cómo son varias las vulnerabilidades detectadas:

![](images/Screenshot_20250217_182724.png)

Además el desarrollador, nos informa de los productos y versiones afectadas y desde dónde nos podemos descargar los parches de seguridad o software con las vulneravilidades ya corregidas.

Vamos a proceder con el trazado de la primera vulnerabilidad presente, en nuestro caso la __CVE-2023-29073__.

Para ver información sobre dicha vulnerabilidad podemos acudir al menos a dos fuentes:

- [La sección de CVE que mantiene cve.org.](https://cve.org)

- [La base de datos de vulnerabilidades de la NVD.](https://nvd.nist.gov/vuln/detail/CVE-2023-29073)

## Información sobre el riesgo o criticidad de una vulnerabilidad

Desde la [entrada correspondiente a la vulnerabilidad en la NVD](https://nvd.nist.gov/vuln/detail/CVE-2023-29073), lo primero que nos encontramos, es la información de la criticidad que la vulnerabilidad presenta, así como el vector asociado a dicho nivel en la CVSS. En este caso vemos que tiene una valoración de 9.8.
 
![](images/Screenshot_20250217_183915.png) 

Si ponemos el cursor sobre el Vector nos aparecerán los valores correspondientes a las diferentes métricas que se han usado para calcularlo.

![](images/Screenshot_20250217_184917.png)

## Información sobre las debilidades explotadas.

Otra información importante a obtener son las debilidades que son explotadas. Podemos obtener también esta información tanto en la información de la NVD como en la de CVE.ORG.

![](images/cwe.png)

En esta ocasión podemos ver como son dos las debilidades explotadas por esta vulnerabilidad: CWE-787 y CWE-122. Vamos a ver información sobre ellas.

- CWE-787

> [Podemos ver información de esta debilidad en la página de cwe.mitre.org](https://cwe.mitre.org/data/definitions/787.html)
>
> Dentro de la información mostrada en dicha página, podemos tener diferentes vistas, tal y como podemos ver en la imagen siguiente. Si le damos a __Complete__ tendremos toda la información visible.
>
> ![](images/cve1.org)
>
> De la información mostrada, podemos extraer, que la debilidad explotada, consiste en la escritura en posiciones fuera de los límites de la memoria, y esto podría ser utilizado para modificar los datos de control, direcciones de retorno e incluso ejecutar código.
>
> Como mitigaciones que nos ofrecen es usar lenguajes donde no se produzca el desbordamiento del buffer o sea más fáciles de evitar. 
>
> También podemos ver las posibles mitigaciones que podemos efectuar en las fases de arquitectura y diseño, como utilizar diferentes librerías y métodos.
>
> Más información a obtener... por ejemplo podemos observar como son debilidades presentes en lenguajes como C y C++, por lo que seguramente la aplicación está escrita en alguno de ellos. ![](images/cwe2.png)
>
> También, por último, podemos ver las relaciones entre ésta y otras debilidades, ya que como podemos ver en la imagen ![](images/cwe3.org), esta debilidad ha surgido a partir de la CWE-119 y es padre de la CWE-121 y CWE-122 que es la otra debilidad presente en la vulnerabilidad que estamos estudiando.


- CWE-122
> [Podemos ver información de esta debilidad en la página de cwe.mitre.org](https://cwe.mitre.org/data/definitions/122.html)
>
> Si leemos, podemos ver cómo nos encontramos ante la debilidad de desbordamiento de pila y que se considera una variación de la anterior debilidad, por lo que es hijo de ella.
>
> También vemos que es una debilidad presente en los lenguajes C y C++ y aquí en está página podemos encontrar la relación de esta debilidad con otro listado el de patrones de ataque. Tal y como vemos en la imagen, ![](images/capec.png) para acometer esta debilidad usamos el patrón de ataque catalogado como CAPEC-92. ![](images/CAPEC.png)

## Información sobre patrones de ataque

Podemos acceder a información sobre los patrones de ataque en la lista mantenida por la Mitre en la dirección [capec.mitre.org](https://capec.mitre.org/)

En el caso que nos atañe, hemos llegado a que la vulnerabilidad que estudiamos se puede explotar mediante el [patrón de ataque CAPEC-92. Aquí tenemos enlace a él.](https://capec.mitre.org/data/definitions/92.html)

Como nos pasaba en la página cwe.mitre.org, aquí también podemos seleccionar la información a mostrar, dependiendo de nuestras necesidades. En caso de que queramos ver toda la información, selecionamos la vista Complete.

> Por la información suministrada, vemos que el ataque se denomina desbordamiento de enteros y consiste en obligar a una variable, dicho valor suele ser una posición de memoria, y utilizando valores fuera del rango de los valores enteros, se le asigna un valor no admitido para forzar un comportamiento inesperado.
>
> Podemos ver cómo se realiza el flujo de ejecución, los requisitos previos, etc. así como las habilidades requeridas para la realización de este patrón de ataque.
>
> Por otra parte también vemos las consecuencias respecto a la integridad, confidencialidad, etc., así como las posibles mitigaciones que podemos realizar.
>
>![](images/capec2.png)

---
## ENTREGA
>__Crea un repositorio  con nombre PPS-Unidad1Actividad1-Tu nombre que contenga las respuestas a las preguntas y las evidencias de que has realizado las operaciones indicadas.__

>__Sube a la plataforma, tanto el repositorio comprimido como la dirección a tu repositorio de Github.__
