---
title: Plantilla de proyecto web de Django para Python
description: Información general de las plantillas de Visual Studio para aplicaciones web escritas en Python con el marco Django.
ms.date: 07/13/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 5c5b64e6f14ef8a6d8015f27252374e54a6dd764
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="django-web-project-template"></a>Plantilla de proyecto web de Django

[Django](https://www.djangoproject.com/) es un marco de Python de alto nivel diseñado para el desarrollo web rápido, seguro y escalable. La compatibilidad de Python en Visual Studio proporciona una plantilla de proyecto para configurar la estructura de una aplicación web basada en Django. Para usar la plantilla en Visual Studio, seleccione **Archivo > Nuevo > Proyecto**, busque "Django" y seleccione la plantilla **Proyecto web de Django**. El proyecto resultante incluye código reutilizable, así como una base de datos de SQLite predeterminada. La plantilla **Proyecto web de Django en blanco** es similar, pero no incluye la base de datos.

Visual Studio proporciona IntelliSense al completo para proyectos de Django:

- Variables de contexto que se pasan en la plantilla:

    ![IntelliSense para variables de contexto](media/template-django-intellisense.png)

- Etiquetado y filtrado para elementos integrados y definidos por el usuario:

    ![IntelliSense para etiquetas y filtros](media/template-django-intellisense-filter.png)

- Color de sintaxis para JavaScript y CSS insertado:

    ![IntelliSense para CSS](media/template-django-intellisense-css.png)

    ![IntelliSense para JavaScript](media/template-django-intellisense-js.png)

Visual Studio también proporciona [compatibilidad con la depuración](debugging-python-in-visual-studio.md) completa para los proyectos de Django: 

![Puntos de interrupción](media/template-django-debugging.png)

Es habitual que los proyectos de Django se administren mediante su archivo `manage.py`, que es una hipótesis que sigue Visual Studio. Si deja de usar ese archivo como el punto de entrada, básicamente divide el archivo del proyecto. En ese caso necesita [volver a crear el proyecto de archivos existentes](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files) sin marcarlo como un proyecto de Django.

## <a name="django-management-console"></a>Consola de administración de Django

El acceso a la consola de administración de Django se realiza a través de varios comandos del menú **Proyecto** o haciendo clic con el botón derecho en el proyecto en el Explorador de soluciones.

- **Abrir Shell de Django**: abre un Shell en el contexto de la aplicación que le permite manipular los modelos

    ![Consola](media/template-django-console-shell.png)

- **Django Sync DB** (Base de datos de sincronización de Django): ejecuta `manage.py syncdb` en una ventana interactiva:

    ![Consola](media/template-django-console-sync-db.png)

- **Collect Static** (Recopilar estáticos): ejecuta `manage.py collectstatic --noinput` para copiar todos los archivos estáticos en la ruta de acceso que especificada `STATIC_ROOT` en `settings.py`. Tenga en cuenta que cuando [publicar en Microsoft Azure](python-web-application-project-templates.md#publishing-to-azure-app-service), automáticamente se recopilan los archivos estáticos como parte de la operación de publicación.

    ![Consola](media/template-django-console-collect-static.png)

- **Validar**: ejecuta `manage.py validate`, que informa de los errores de validación en los modelos instalados que especifica `INSTALLED_APPS` en `settings.py`:

    ![Consola](media/template-django-console-validate.png)