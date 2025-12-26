# Cómo consumir APIs con Retrofit utilizando MVVM, Dagger Hilt y Corrutinas

Este proyecto presenta una **guía educativa de desarrollo Android moderno**, enfocada en el consumo de APIs REST utilizando buenas prácticas y una arquitectura profesional.  
El objetivo es enseñar a estudiantes cómo estructurar correctamente una aplicación Android escalable, mantenible y preparada para proyectos reales.

---

## 📌 Descripción general

El desarrollo Android actual requiere:

- Comunicación eficiente con APIs REST
- Manejo correcto de procesos asíncronos
- Separación clara de responsabilidades
- Código desacoplado y fácil de mantener

En este proyecto se explica paso a paso cómo lograrlo utilizando **Retrofit**, **corrutinas de Kotlin**, la arquitectura **MVVM** y **Dagger Hilt** para la inyección de dependencias.

---

## 🎯 Objetivos del proyecto

- Comprender cómo consumir APIs REST en Android
- Aplicar arquitectura MVVM correctamente
- Utilizar corrutinas respetando el ciclo de vida
- Implementar inyección de dependencias con Dagger Hilt
- Construir una base reutilizable para aplicaciones reales

---

## 🧠 Conceptos fundamentales

### 🔹 Consumo de APIs REST
Retrofit permite realizar llamadas HTTP de forma sencilla, manejando automáticamente la conversión de respuestas JSON a objetos Kotlin mediante Gson.

### 🔹 Modelado de datos
Los datos recibidos desde la API se representan mediante `data class` que reflejan exactamente la estructura del JSON.

| Campo   | Tipo   | Descripción                    |
|--------|--------|--------------------------------|
| userId | Int    | Identificador del usuario      |
| id     | Int    | Identificador del recurso      |
| title  | String | Título del contenido           |
| body   | String | Contenido principal            |

### 🔹 Corrutinas y ciclo de vida
Las corrutinas permiten ejecutar tareas en segundo plano sin bloquear la interfaz de usuario.

| Scope            | Uso principal                          |
|------------------|----------------------------------------|
| lifecycleScope  | Ejecución segura ligada a la vista     |
| viewModelScope  | Lógica de negocio en ViewModel         |

---

## 🏗️ Arquitectura MVVM

La arquitectura MVVM divide la aplicación en capas bien definidas:

| Capa        | Responsabilidad                         |
|------------|------------------------------------------|
| Model      | Representa los datos                     |
| Repository | Gestiona el acceso a la fuente de datos  |
| ViewModel | Contiene la lógica de la UI              |
| View       | Muestra la información al usuario        |

Este enfoque mejora la organización del código, facilita las pruebas y permite escalar el proyecto sin problemas.

---

## 🧪 Ejercicios prácticos

### 🧩 Ejercicio 1: App de publicaciones

**Descripción:**  
Aplicación Android que consume publicaciones desde una API REST y las muestra en una lista.

**Tecnologías:**
- Kotlin  
- Retrofit  
- Corrutinas  
- MVVM  
- JSONPlaceholder  

**Funcionalidades:**
- Obtener datos desde `/posts`
- Mostrar título y contenido
- Contar el número de publicaciones

**Modelo de datos:**
```kotlin
data class Post(
    val userId: Int,
    val id: Int,
    val title: String,
    val body: String
)
```
🧩 Ejercicio 2: Probador de APIs REST
📝 Descripción

Este ejercicio consiste en desarrollar una aplicación Android que permita consumir distintos endpoints de una API REST y visualizar sus respuestas en pantalla.
El objetivo es aprender a manejar múltiples solicitudes HTTP, organizar el código correctamente y controlar los estados de carga y error.

Este tipo de aplicación se usa en proyectos reales como:

Herramientas internas de prueba de APIs

Apps educativas

Dashboards de desarrollo

🔧 Tecnologías utilizadas

Kotlin – Lenguaje principal de desarrollo

Retrofit – Consumo de servicios REST

Corrutinas – Manejo de procesos asíncronos

MVVM – Arquitectura de la aplicación

Gson – Conversión de JSON a objetos

JSONPlaceholder – API REST de prueba

📱 Funcionalidades

Consumo de los siguientes endpoints:

/posts

/users

/comments

Mostrar datos en listas

Manejar estados de:

Cargando

Éxito

Error

Separación clara de responsabilidades

🧱 Ejemplo de interfaz Retrofit
interface ApiService {

    @GET("posts")
    suspend fun getPosts(): List<Post>

    @GET("users")
    suspend fun getUsers(): List<User>

    @GET("comments")
    suspend fun getComments(): List<Comment>
}

🧩 Ejercicio 3: Proyecto académico con arquitectura MVVM
📝 Descripción

En este ejercicio se desarrolla una aplicación Android aplicando correctamente la arquitectura MVVM (Model – View – ViewModel), uno de los patrones más utilizados en el desarrollo Android moderno.

El objetivo principal es separar la lógica de negocio de la interfaz de usuario, permitiendo que la aplicación sea más mantenible, escalable y fácil de probar.

Este ejercicio refuerza conceptos clave como:

Organización por capas

Manejo del ciclo de vida

Observación de datos reactivos

🔧 Tecnologías utilizadas

Kotlin

Arquitectura MVVM

ViewModel

LiveData

Corrutinas

Retrofit

Dagger Hilt

📱 Funcionalidades implementadas

Obtención de datos desde una API REST

Manejo de la lógica de negocio desde el ViewModel

Observación de datos con LiveData

Comunicación limpia entre capas

Inyección de dependencias con Dagger Hilt

🧠 Ejemplo de ViewModel
@HiltViewModel
class PostViewModel @Inject constructor(
    private val repository: PostRepository
) : ViewModel() {

    val posts = liveData {
        emit(repository.getPosts())
    }
}

🧩 Ejercicio 4: Base para aplicación Android real
📝 Descripción

En este ejercicio se construye una base sólida y reutilizable para el desarrollo de aplicaciones Android reales, aplicando una arquitectura moderna y buenas prácticas de desarrollo de software.

El objetivo es crear una estructura inicial que pueda servir como plantilla base para futuros proyectos, permitiendo escalar la aplicación sin perder orden, rendimiento ni mantenibilidad.

🔧 Tecnologías utilizadas

Kotlin

Retrofit

Corrutinas

Arquitectura MVVM

Dagger Hilt

JSONPlaceholder (API de pruebas)

📱 Funcionalidades implementadas

Estructura del proyecto organizada por capas

Separación clara de responsabilidades

Acceso centralizado a datos mediante Repository

Comunicación con API REST

Base lista para proyectos reales y comerciales

🧱 Ejemplo de Repository
class PostRepository @Inject constructor(
    private val api: ApiService
) {

    suspend fun getPosts() = api.getPosts()

}

🧠 Conclusión

El desarrollo de aplicaciones Android modernas requiere mucho más que solo hacer que la app funcione. A lo largo de estos ejercicios prácticos se demuestra la importancia de aplicar buenas prácticas de arquitectura, manejo correcto del ciclo de vida y uso de herramientas estándar de la industria.

El uso de Retrofit junto con corrutinas de Kotlin permite crear aplicaciones eficientes y responsivas. La implementación de la arquitectura MVVM garantiza una correcta separación de responsabilidades, facilitando el mantenimiento, las pruebas y la escalabilidad del proyecto.

La integración de Dagger Hilt reduce el acoplamiento entre clases y mejora la organización del código, acercando el proyecto a un nivel profesional.

En conclusión, este enfoque proporciona una estructura reutilizable, escalable y alineada con los estándares actuales del desarrollo Android.
