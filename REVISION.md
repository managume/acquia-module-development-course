# Revisión de compatibilidad con Drupal 9

## Lección 18: Crear módulo RSVP / Create RSVP module

En Drupal 8 se hacía uso del atributo `core` para designar la compatibilidad con Drupal. En Drupal 9 se recomienda el uso de `core_version_requirement` que nos permite el uso de *constraints*.

Ejemplo:

```yml
name: Ejemplo core_version_requirement
description: Este es un ejemplo del uso de core_version_requirement en vez de core.
package: Ejemplos
version: 1.0
#core: 8.x
core_version_requirement: ^8.8.0 || ^9.0
```

## Lección 19: Introducción a la construcción de Formularios / Intro to Form Building

Puedes consultar la API con los diferentes elementos de formulario para Drupal 9.x en el [siguiente enlace](https://api.drupal.org/api/drupal/elements/9.0.x)

Si estás interesado en una versión concreta de la API puedes editar la url `https://api.drupal.org/api/drupal/elements/9.0.x` cambiando la versión *Major* y/o *Minor*.

Indicar brevemente que la nomenclatura de versionado en Drupal se construye de la siguiente manera: *Major*.*Minor*.*Patch*.

Ejemplo:

Para la versión 9.1.2 tenemos la siguiente relación.

* Mayor/Major = 9
* Menor/Minor = 1
* Parche/Patch = 2


## Lección 20: Construir Formulario RSVP / Build RSVP Form

En la función método `submitForm` se hace uso del método `drupal_set_message` deprecado en las últimas versiones de Drupal 8.

En vez de dicho método, utilizaremos:

```php
\Drupal::messenger()->addMessage()
```

Ejemplo:

```php
public function submitForm(array &$form, FormStateInterface $form_state)
{
    \Drupal::messenger()->addMessage(t('The form is working'));
}
```