# Sistema de registro de asistencias
Aplicación web desarrollada para un trabajo de Programación Orientada a Objetos, con Flask y SQLAlchemy para registrar la entrada y salida de empleados, consultar registros y generar informes.

## Funcionalidades

- Registrar la entrada de un empleado mediante su legajo y los últimos dígitos de su DNI.
- Registrar la salida de un empleado que tenga una entrada abierta en el día.
- Consultar registros de horario de un empleado entre dos fechas.
- Consultar informes generales por período, función y dependencia.
- Consultar un informe personal con el total de horas registradas.

La aplicación utiliza las funciones `AD`, `DO` y `TE` para clasificar trabajadores; la función `AD` se usa para validar el acceso a los informes.

## Tecnologías

- Python
- Flask
- Flask-SQLAlchemy
- SQLite
- HTML, Jinja y CSS

## Estructura

```text
proyectoPOO/
├── app.py
├── config.py
├── models.py
├── instance/
│   └── datos.sqlite3
├── static/
│   └── css/
└── templates/
    ├── base_template.html
    ├── inicio.html
    ├── registrar_entrada.html
    ├── registrar_salida.html
    ├── consultar_registros.html
    ├── gen_inf_general.html
    └── gen_inf_personal.html
```

`models.py` define dos entidades relacionadas:

- **Trabajador**: datos identificatorios, legajo, función y relación con sus registros.
- **RegistroHorario**: fecha, hora de entrada, hora de salida, dependencia y trabajador asociado.

## Requisitos

- Python 3 instalado.
- `pip`.

## Instalación y ejecución

Desde una terminal, situarse en la carpeta `proyectoPOO`:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install Flask Flask-SQLAlchemy
python app.py
```

En Windows, si PowerShell impide activar el entorno virtual, se puede ejecutar la aplicación usando directamente:

```powershell
.\.venv\Scripts\python.exe -m pip install Flask Flask-SQLAlchemy
.\.venv\Scripts\python.exe app.py
```

La aplicación se inicia en `http://127.0.0.1:5000`.

## Base de datos

La configuración de `config.py` usa SQLite. Flask-SQLAlchemy resuelve `sqlite:///datos.sqlite3` en la carpeta `instance`, por lo que la aplicación espera la base de datos en `instance/datos.sqlite3`.

El archivo de base de datos debe contener las tablas y los datos de trabajadores necesarios. La aplicación no crea las tablas automáticamente al iniciarse. Los scripts SQL incluidos en la carpeta documentan operaciones relacionadas con la base de datos.

## Seguridad antes de publicar o desplegar

- `config.py` contiene una clave secreta de ejemplo. Reemplázala por una clave privada, mantenla fuera del repositorio y cárgala mediante una variable de entorno.
- La base de datos puede contener DNI, correos u otros datos personales. No publiques datos reales; utiliza una base de datos de prueba anonimizada o excluye el archivo de SQLite del repositorio.
- El servidor de desarrollo de Flask no está destinado a producción.

## Estado

Proyecto académico en desarrollo. La aplicación está orientada al registro local de asistencia y no incluye una API ni un proceso de despliegue para producción.
