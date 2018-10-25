---
title: Django-Webprojektvorlage für Python
description: Übersicht der Visual Studio-Vorlagen für mithilfe des Django-Frameworks in Python geschriebene Webanwendungen.
ms.date: 07/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 4ea90a97067e92d39772bd4257dc3abbae58d1d8
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100964"
---
# <a name="django-web-project-template"></a>Vorlage „Django-Webprojekt“

[Django](https://www.djangoproject.com/) ist ein allgemeines Python-Framework für die schnelle, sichere und skalierbare Webentwicklung. Die Python-Unterstützung in Visual Studio enthält mehrere Projektvorlagen zum Einrichten der Struktur einer Django-basierten Webanwendung. Sie können in Visual Studio Vorlagen verwenden, indem Sie auf **Datei** > **Neu** > **Projekt** klicken, nach „Django“ suchen und eine der Vorlagen **Leeres Django-Webprojekt**, **Django-Webprojekt** und **Fragt ein Django-Webprojekt ab** auswählen. Eine exemplarische Vorgehensweise für alle Vorlagen finden Sie im [Django-Tutorial](learn-django-in-visual-studio-step-01-project-and-solution.md).

Visual Studio bietet vollständiges IntelliSense für Django-Projekte:

- An die Vorlage übergebene Kontextvariablen:

    ![IntelliSense für Kontextvariablen](media/template-django-intellisense.png)

- Markierungen und Filter sowohl für integrierte als auch für benutzerdefinierte Variablen:

    ![IntelliSense für Tags und Filter](media/template-django-intellisense-filter.png)

- Syntaxfarben für eingebettetes CSS und JavaScript:

    ![CSS-IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio bietet außerdem vollständige [Debugunterstützung](debugging-python-in-visual-studio.md) für Django-Projekte: 

![Haltepunkte](media/template-django-debugging.png)

Django-Projekte werden in der Regel über ihre *manage.py*-Datei verwaltet. Visual Studio folgt dieser Annahme. Wenn Sie diese Datei nicht mehr als Einstiegspunkt verwenden, zerstören Sie die Projektdatei. In diesem Fall müssen Sie [das Projekt aus vorhandenen Dateien neu erstellen](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files), ohne es als ein Django-Projekt zu kennzeichnen.

## <a name="django-management-console"></a>Django-Verwaltungskonsole

Sie können über verschiedene Befehle im Menü **Projekt** oder durch Rechtsklick auf das Projekt im **Projektmappen-Explorer** auf die Django-Verwaltungskonsole zugreifen.

- **Django-Shell öffnen**: Öffnet eine Shell im Kontext Ihrer Anwendung, damit Sie Ihre Modelle bearbeiten können:

    ![Konsole](media/template-django-console-shell.png)

- **Django-DB synchronisieren**: Führt `manage.py syncdb` in einem **interaktiven** Fenster aus:

    ![Konsole](media/template-django-console-sync-db.png)

- **Statische Dateien erfassen**: führt `manage.py collectstatic --noinput` aus, um alle statischen Dateien in den durch `STATIC_ROOT` angegebenen Pfad in Ihrer *settings.py*-Datei zu kopieren.

    ![Konsole](media/template-django-console-collect-static.png)

- **Überprüfen**: führt `manage.py validate` aus, wodurch Überprüfungsfehler in den installierten Modellen gemeldet werden, die durch `INSTALLED_APPS` in Ihrer *settings.py*-Datei angegeben wurden:

    ![Konsole](media/template-django-console-validate.png)

## <a name="see-also"></a>Siehe auch

- [Django-Tutorial](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Veröffentlichen in Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
