## Pasos de despliegue

1. **Registro en Azure**
   Ingresar a [azure.microsoft.com](https://azure.microsoft.com/es-es/free/students) y crear
   una cuenta con la cuenta institucional. Completar la verificación de identidad estudiantil
   para activar los beneficios.

2. **Canjear créditos**
   Desde el panel de beneficios, canjear los $200 USD en créditos de Azure for Students
   disponibles para usar en los servicios de la plataforma.

3. **Repositorio en GitHub**
   Crear el repositorio `pokedexsdla` en GitHub, subir el proyecto suministrado por el
   profesor y hacer push a la rama `main`.

4. **Crear la Static Web App en Azure**
   Ingresar al [Portal de Azure](https://portal.azure.com), buscar **Static Web App** y
   completar el formulario vinculando el repositorio `pokedexsdla`. Configurar los parámetros
   de build con `output location: dist/pokedex-angular`. Azure genera automáticamente el
   pipeline de CI/CD con GitHub Actions.

    **Conectar con GitHub**
   Autorizar a Azure para acceder a GitHub, seleccionar el repositorio `pokedexsdla` y la
   rama `main`. Configurar los parámetros de build:

   | Campo | Valor |
   |---|---|
   | App location | `/` |
   | Api location | *(dejar vacío)* |
   | Output location | `dist/pokedex-angular` |

   Hacer clic en **"Revisar y crear"** → **"Crear"**. Azure genera automáticamente el pipeline
   de CI/CD con GitHub Actions que despliega la aplicación en cada nuevo commit.

---

## Errores encontrados

### ❌ Imágenes no se mostraban en producción

Las cards de Pokémon aparecían sin imagen luego del despliegue, aunque en local funcionaban
correctamente. Revisando con DevTools (F12 → Elements) se encontró que las rutas apuntaban a
`/pokedex-angular/assets/images/`, una ruta que no existe en el servidor de Azure.

La causa estaba en `environment.prod.ts`:

```typescript
// Incorrecto
imagesPath: '/pokedex-angular/assets/images',

// Correcto
imagesPath: '/assets/images',
```

Después de corregirlo y hacer push, las imágenes cargaron correctamente. ✅

---

### Advertencias de budget en el build

El pipeline mostró advertencias porque el tamaño del bundle superaba el límite configurado
en `angular.json`: