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
