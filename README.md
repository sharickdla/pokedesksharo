# Pokédex — Despliegue en Azure 

## Pasos de despliegue

1. **Registro en Azure**
   Ingresar a [azure.microsoft.com](https://azure.microsoft.com/es-es/free/students) y hacer clic en
   "Empiece gratis". Me auntentiqúé con una cuenta personal
    para activar la cuenta.

2. **Canjear créditos**
   Una vez activa la cuenta, activé los 200 créditos.
   

3. **Repositorio en GitHub**
   Crear un repositorio público llamado `pokedexsdla` en GitHub. Clonar el repositorio de forma
   local, copiar el proyecto suministrado por el profesor y hacer push a la rama `main` para
   tener el código disponible en la nube.

4. **Despliegue en Azure**
   Ingresar al [Portal de Azure](https://portal.azure.com) y seleccionar "Crear un recurso".
   Buscar **Static Web App**, completar el formulario con los datos del proyecto y vincular la
   cuenta de GitHub para que Azure tenga acceso al repositorio `pokedexsdla`. Seleccionar la
   rama `main` y configurar los parámetros de build. Al finalizar, Azure genera automáticamente
   un pipeline de CI/CD con GitHub Actions que despliega la aplicación en cada nuevo commit.