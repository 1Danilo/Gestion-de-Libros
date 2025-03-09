# Sistema de Gestión de Libros 📚

Este proyecto es una aplicación web que permite a los usuarios registrarse, iniciar sesión y gestionar una colección de libros. La aplicación se divide en dos partes principales:

- **Frontend:** Desarrollado en React con Material UI, utiliza Context API para gestionar el estado de autenticación, React Router para la navegación y Axios para comunicarse con el backend. ⚛️🎨
- **Backend:** Implementado con FastAPI y SQLite (ideal para desarrollo y pruebas), utiliza SQLAlchemy para interactuar con la base de datos y Pydantic para la validación de datos. Se incluyen operaciones CRUD para usuarios y libros, junto con la funcionalidad de login y filtrado de libros por usuario autenticado. 🚀💾

---

## Requisitos Funcionales ✅

1. **Página de Inicio:**  
   - Se muestra una página principal con una barra de navegación que contiene un botón **"Login"**.

2. **Autenticación:**  
   - Al presionar **"Login"**, se muestra un formulario que solicita el nombre de usuario (email) y la contraseña.  
   - Se valida el formato del email y se verifican las credenciales en la base de datos.  
   - Si las credenciales son incorrectas, se muestra un mensaje de error ❌.  
   - Si son correctas, la barra de navegación se actualiza mostrando los botones **"Mis Libros"** y **"Desconectar"** 🔓.

3. **Listado de Libros:**  
   - Al presionar **"Mis Libros"**, se muestra una tabla paginada con las columnas **"Nombre"**, **"Descripción"** y **"Acciones"**.  
   - Se listan los libros desde la base de datos, mostrando solo 10 libros por página.  
   - Se implementa paginación para navegar entre las distintas páginas 🔄.

4. **Agregar Libro:**  
   - Encima de la tabla de libros se incluye un botón **"Agregar Libro"**.  
   - Al presionar el botón, se abre un modal que solicita el nombre y la descripción del libro.  
   - Dentro del modal se incluye un botón **"Agregar"** para añadir el nuevo libro a la base de datos ➕.

5. **Acciones en la Tabla de Libros:**  
   - En la columna **"Acciones"** se incluyen botones **"Editar"** y **"Eliminar"**.  
   - Al presionar **"Editar"**, se abre un modal que muestra los datos actuales del libro y permite realizar cambios, los cuales se guardan en la base de datos.  
   - Al presionar **"Eliminar"**, se muestra un modal de confirmación antes de eliminar el libro de la base de datos 🗑️.

---

## Requisitos Técnicos 🛠️

### Frontend
- **React.js** para construir la interfaz de usuario.
- **Material UI** para el diseño visual y componentes.
- **Context API** para gestionar el estado de autenticación.
- **React Router** para el enrutamiento.
- **Axios** para realizar llamadas al backend.

### Backend
- **FastAPI** para la creación de APIs REST.
- **SQLite** para almacenar la información (ideal para desarrollo y pruebas).
- **SQLAlchemy** para la interacción con la base de datos.
- **Pydantic** para la validación y serialización de datos.
- Las contraseñas se almacenan de forma segura utilizando técnicas de hashing (bcrypt).

---

## Arquitectura y Funcionalidades del Backend 🔙

### Base de Datos
- Se crea una base de datos con **SQLite** (archivo `libros.db`).
- Se crean dos tablas: **Usuarios** y **Libros**.
  - **Usuarios:**  
    Contiene campos: `nombre`, `email` (usado como login) y `hashed_password`.
  - **Libros:**  
    Contiene campos: `nombre`, `descripcion` y `propietario_id`, estableciendo una relación de uno a muchos (un usuario puede tener varios libros).

### Modelos y Esquemas
- Se definen modelos de SQLAlchemy en `models.py` para reflejar la estructura de la base de datos.
- Se utilizan esquemas Pydantic (en `schemas.py`) para validar y serializar la entrada y salida de datos.

### Operaciones CRUD
- Se implementan endpoints para crear, leer, actualizar y eliminar registros tanto de usuarios como de libros.
  - **Registro:** El endpoint `/register` permite la creación de nuevos usuarios.
  - **Login:** El endpoint `/token` permite la autenticación de usuarios verificando el hash de la contraseña.
  - **Libros:** Los endpoints de libros están protegidos y filtran los libros según el usuario autenticado.

---

## Arquitectura y Funcionalidades del Frontend 🔜

### Página de Inicio y Navegación
- Una página principal muestra un mensaje de bienvenida.
- El **Navbar** muestra botones de **"Login"** y **"Regístrate"** cuando no hay usuario autenticado, y **"Mis Libros"** y **"Desconectar"** cuando el usuario ha iniciado sesión.

### Autenticación
- Un formulario de **Login** permite a los usuarios autenticarse.
- Se utiliza Context API para gestionar el estado de autenticación y se realizan llamadas al backend utilizando Axios.

### Gestión de Libros
- La página de **"Mis Libros"** muestra un listado paginado de libros asociados al usuario.
- Se incluye la funcionalidad para agregar, editar y eliminar libros mediante modales.
- La comunicación con el backend se realiza a través de Axios, utilizando el token de autenticación.

---

## Cómo Ejecutar el Proyecto 🚀

### Backend

Asegúrate de tener instalados los siguientes paquetes:

- FastAPI
- Uvicorn
- SQLAlchemy
- psycopg2 (o psycopg2-binary)
- passlib
- Otros paquetes necesarios

**Instalar Dependencias:**

```bash
pip install -r requirements.txt

**Ejecutar el Servidor:**

```bash
uvicorn main:app --reload


### Frontend

**Instalar Dependencias:**

Navega a la carpeta del "frontend" y ejecuta:

npm install

Ejecutar el Servidor de Desarrollo:

npm run dev


