# Bootcamp GitHub Actions: Inauguración y Clase de Conceptos Fundamentales

> [!NOTE]
> 05/29/2025 | 1,700 personas asistierón.

El objetivo de este bootcamp es que aprendas a usar GitHub Actions para automatizar tus flujos de trabajo de desarrollo. A lo largo de las siguientes semanas, exploraremos cómo configurar, personalizar y optimizar tus acciones en GitHub.

Posibilidad de conseguir un certificado al finalizar el bootcamp de la mano de Microsoft (solo 200).

Requisitos:

- Asistir a todas las clases del bootcamp o ver las grabaciones. (10 sesiones)
- Casi al terminar las clases, se habilitara un 2do filtro dentro de la plataforma para asi poder intentar acceder al certificado.

> [!NOTE]
> Cada certificado cuesta al rededor de 99 USD, por lo que es un gran beneficio para los participantes del bootcamp.

Daran un certificado de participación a todos los que asistan a todas las clases por parte de CodigoFacilito.

## ¿Que es GitHub Actions?

Github actions es una herramienta de Github que nos ayuda a automatizar tareas relacionadas a nuestro repositorio.

- CI (CONTINUOUS INTEGRATION)
- CD (CONTINUOUS DEPLOYMENT)

## ¿Cómo funciona?

Github Actions nos permite crear Workflows que sera ejecutados en eventos especificos.

- Push
- Merge
- PR

## Casos de uso

Automatización.

- Build
- Testing.
- Notificaciones (Slack, Notion, Correos, Asana...).
- Escaneo de seguridad.
- ...

## Conceptos claves

- **Workflow**: Conjunto de procesos automatizados definidos en un archivo YAML dentro de `.github/workflows`.
- **Triggers**:
  - Eventos que hacen que el workflow se ejecute.
  - Se define utilizando `on`.
- **Jobs**: Unidades independientes de trabajo dentro de un workflow.
  - Se ejecutan de paralelo por defecto.
  - Cada Job corre en un `runner`.
  - Se definen utilizando `jobs`.
- **Steps**:
  - Pasos individuales dentro de un Job.
  - Un Job puede posser multiples pasos.
  - Se ejecutan secuencialmente en el mismo runner.
  - Tiene la capacidad de usar variables de entorno.
  - De definir utilizando `steps`.
    - Utilizan _name_, _uses_ / _run_
  - Se ejecutan de forma secuencial.
  - Pueden usar variables de entorno o secrets.
- **Runners**: Entornos (Maquinas Virtuales) donde se ejecutan los jobs.
  - Github posee imagenes utilizando de S.O como Ubuntu, Windows y MacOS.
  - Se definen utilizando `runs-on`.

## Ventajas

- Gratuito.
- No require configuración externa.
- Ecosistema extenso: +10,000 acciones en el catalogo.

## Ejemplo

```yml
# Nombre del workflow
name: CI Pipeline

# Cuando pase `push` sobre cualquier rama
on: [push]

jobs:
  # Nombre del Job
  build-and-test:
    # SO
    runs-on: ubuntu-latest
    # Pasos a ejecutar
    steps:
      # Chequea el código del repositorio
      # Uses es para ejecutar una acción que alguien mas ya ha creado
      - uses: actions/checkout@v4
      # Instala las dependencias del proyecto
      - run: npm install
      # Corre las pruebas
      - run: npm test
      # Imprime un mensaje de éxito
      - run: echo "✅ Todo listo!"
```
