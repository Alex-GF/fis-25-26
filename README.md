# Autoadaptación Dirigida por Planes de Precios (Pricing-Driven Self-Adaptation)

## 📚 Índice

1. [🧭 ¿Por qué existe este repositorio?](#-por-qu%C3%A9-existe-este-repositorio)
    
2. [🎯 Competencias que adquirirás](#-competencias-que-adquir%C3%A1s)
    
3. [🚀 ¿Dónde está la dificultad?](#-d%C3%B3nde-est%C3%A1-la-dificultad)
    
4. [🔧 ¿Cómo lo abordamos?](#-c%C3%B3mo-lo-abordamos)
    
    - [🧩 1. Modelar el pricing como artefacto ejecutable](#-1-modelar-el-pricing-como-artefacto-ejecutable)
        
    - [🏗️ 2. Diseñar una arquitectura que haga cumplir el iPricing en tiempo real](#%25EF%25B8%258F-2-dise%C3%B1ar-una-arquitectura-que-haga-cumplir-el-ipricing-en-tiempo-real)
        
5. [✅ Criterios de éxito del alumno](#-criterios-de-%C3%A9xito-del-alumno)
    
6. [🧭 ¿Qué solución proponemos?](#-qu%C3%A9-soluci%C3%B3n-proponemos)


## 🧭 ¿Por qué existe este repositorio?

El desarrollo de aplicaciones _Cloud-Native_ (CNA) ya no consiste solo en desplegar funcionalidades. En el mercado actual, el éxito de una aplicación depende de su **capacidad para adaptarse automáticamente a las necesidades del negocio y a la competencia**.

Estas necesidades se expresan, principalmente, mediante su **estructura de precios (pricing)**, que define:

- Qué características se ofrecen
    
- En qué planes o configuraciones
    
- Con qué límites de uso
    
- A qué precio y bajo qué condiciones  

Los _pricings_ se han convertido en un elemento central del negocio digital. Estudios recientes demuestran no solo que el número de configuraciones posibles en aplicaciones SaaS ha crecido **más de un 200% en los últimos años**, impulsado principalmente por el aumento de _add-ons_; sino que además los _pricings_ son altamente **volátiles**, es decir, cambian con frecuencia para adaptarse al mercado y a la competencia. Esta combinación de complejidad y volatilidad ha generado un problema real en la industria:

> [!WARNING]
> **Los sistemas actuales no pueden adaptarse automáticamente cuando cambia el pricing.** Cada modificación debe implementarse manualmente por los desarrolladores, generando una de los peores tipos de deuda técnica, que provoca: despliegues lentos, errores recurrentes y pérdida directa de competitividad.

Este repositorio ha sido creado para enseñarte, como futuro ingeniero/a, a **transformar un pricing de una tabla comercial estática a un artefacto capaz de controlar automáticamente el comportamiento de una aplicación cloud-native**. Es decir, aprenderás a usar el pricing como **motor de autoadaptación en tiempo real**, capaz de dirigir el desarrollo, la operación y la evolución del sistema sin intervención manual.

A esta nueva forma de construir software la llamamos: **Pricing-Driven Self-Adaptation**.


## 🎯 Competencias que adquirirás

Al implementar este paradigma en vuestro proyecto, desarrollaréis las siguientes habilidades clave:

| **Competencia**                                        | **Descripción**                                                                                                                       |
| ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- |
| **Definir planes de precios como artefactos software** | Diseñar, representar y validar un pricing real utilizando la tecnología de SPHERE.                                                    |
| **Autoadaptación dirigida por planes de precios**      | Instrumentar una aplicación cloud-native para que adapte dinámicamente sus funcionalidades utilizando SPACE como motor de evaluación. |


## 🚀 ¿Dónde está la dificultad?

En una CNA típica, los planes de precios afectan directamente al comportamiento del sistema: qué funcionalidades tiene cada usuario, cuántas veces puede utilizarlas, qué garantías recibe, etc. Sin embargo, cuando el pricing cambia, **los ingenieros deben modificar manualmente el código, el despliegue, la infraestructura y las políticas de acceso**.

Según el análisis de más de 240 aplicaciones SaaS de distintos sectores (GitHub, Zoom, Salesforce, etc.):

- El número medio de _features_ por pricing ha aumentado un **98% desde 2019**
    
- El número de _add-ons_ ha crecido **más del 200%**, lo que provoca un incremento exponencial de configuraciones posibles
    
- **Ninguna herramienta industrial** actual soporta completamente la autoadaptación basada en _pricing_  

⚡ Esto convierte al _pricing-driven self-adaptation_ en un reto técnico real, de frontera y altamente relevante para la ingeniería de software del presente y del futuro.


## 🔧 ¿Cómo lo abordamos?

  
Este reto debe abordarse con **fundamentos de ingeniería del software**. Para ello, se debe seguir un enfoque sistemático en dos etapas:


### 🧩 1. Modelar el pricing como artefacto ejecutable

El primer paso es **transformar el pricing de un documento comercial estático** (normalmente redactado para el usuario final), **a un artefacto formal, "machine-oriented" y operable en tiempo de ejecución**.
  
Este artefacto se denomina **iPricing** (_intelligent pricing_) y permite que la aplicación entienda:

- Qué planes existen y qué funciones habilita cada uno

- Qué límites de uso se aplican

- Qué add-ons pueden complementar a cada plan

- Opciones de facturación

- ...


### 🏗️ 2. Diseñar una arquitectura que haga cumplir el iPricing en tiempo real

Una vez tenemos el iPricing, hay que diseñar una arquitectura que permita a la CNA adaptarse dinámicamente a lo que este modelo define. Esta solución debe resolver cuatro desafíos esenciales:

**1. Evaluación de acceso instantánea**

> [!NOTE]
> _¿Puede el usuario U acceder a la funcionalidad F?_


Cualquier microservicio debe poder responder a esta pregunta en tiempo real mediante llamadas como:

```ts
isFeatureAvailable("my-feature", "userId")
```

Esta las condiciones detrás de esta decisión no se programarán manualmente, si no que han de inferirse del iPricing y del contrato del usuario.


**2. Sincronización del estado de los contratos**

El sistema debe conocer en todo momento cuánto está utilizando cada usuario sus funcionalidades (es decir, el estado de cada contrato), independientemente del servicio o microservicio que las gestione.

Esto evita desincronizaciones que podrían permitir accesos indebidos o denegar accesos válidos.


**3. Seguridad**

La información sobre permisos de acceso debe propagarse de forma segura entre todos los componentes de la CNA, incluido el frontend.

> [!WARNING]
> No puede ser manipulable por el usuario final ni por ataques intermedios, ya que eso permitiría activar funcionalidades no contratadas.


**4. Cambios en tiempo real sin redespliegue**

Cuando el proveedor actualiza el pricing (por ejemplo, añade un nuevo add-on o cambia un límite de uso), la arquitectura debe:

- Actualizar automáticamente el iPricing (idealmente guardando una copia de la versión del mismo que ha sido sustituída)
    
- Propagar el cambio a toda la aplicación **sin necesidad de realizar un nuevo despliegue**


## ✅ Criterios de éxito del alumno

Para superar este módulo en la asignatura, tu proyecto deberá ser capaz de dar soporte a las siguientes historias de usuario (bien haciendo uso del ecosistema que ponemos a tu disposición, o a través de tu propia solución):

- **Como** usuario **quiero** seleccionar cualquier subscripción válida disponible en el plan de precios **para** usar la configuración que mejor satisface mis necesidades y se alinea con mi presupuesto.
- **Como** stackeholder de la CNA **quiero** modificar el pricing y que los cambios se apliquen automáticamente **para** mejorar la flexibilidad y capacidad de adaptación de la CNA.


## 🧭  ¿Qué solución proponemos?

TO BE WRITTEN
