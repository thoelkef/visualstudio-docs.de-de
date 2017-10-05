---
title: "Django-Webprojektvorlage für Python in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 7/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c479be58-13eb-4d77-9a27-c97ddc290963
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 242203505dc80c9cdfe6041fbf97308a16ccd2c8
ms.contentlocale: de-de
ms.lasthandoff: 07/18/2017

---

# <a name="django-web-project-template"></a>Django-Webprojektvorlage

[Django](https://www.djangoproject.com/) ist ein allgemeines Python-Framework für die schnelle, sichere und skalierbare Webentwicklung. Die Python-Unterstützung in Visual Studio enthält eine Projektvorlage zum Einrichten der Struktur einer Django-basierten Webanwendung. Um die Vorlage in Visual Studio zu verwenden, wählen Sie **Datei > Neu > Projekt**, suchen Sie nach „Django“, und wählen Sie die Vorlage „Django-Webprojekt“ aus. Das resultierende Projekt umfasst Codebausteine sowie eine SQLite-Standarddatenbank. Die Vorlage „Leeres Django-Webprojekt“ ist ähnlich, enthält jedoch nicht die Datenbank.

Visual Studio bietet vollständiges IntelliSense für Django-Projekte:

- An die Vorlage übergebene Kontextvariablen:

    ![IntelliSense für Kontextvariablen](media/template-django-intellisense.png)

- Markierungen und Filter sowohl für integrierte als auch für benutzerdefinierte Variablen:

    ![IntelliSense für Tags und Filter](media/template-django-intellisense-filter.png)

- Syntaxfarben für eingebettetes CSS und JavaScript:

    ![CSS-IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)


Visual Studio bietet außerdem vollständige [Debugunterstützung](debugging.md) für Django-Projekte: 

![Haltepunkte](media/template-django-debugging.png)

Es ist typisch für Django-Projekte, über ihre `manage.py`-Datei verwaltet zu werden. Visual Studio folgt dieser Annahme. Wenn Sie diese Datei nicht mehr als Einstiegspunkt verwenden, zerstören Sie die Projektdatei. In diesem Fall müssen Sie [das Projekt aus vorhandenen Dateien neu erstellen](python-projects.md#creating-a-project-from-existing-files), ohne es als ein Django-Projekt zu kennzeichnen.


## <a name="django-management-console"></a>Django-Verwaltungskonsole

Die Django-Verwaltungskonsole bietet Zugriff über verschiedene Befehle im Menü **Projekt** oder durch Rechtsklick auf das Projekt im Projektmappen-Explorer.

- **Django-Shell öffnen**: Öffnet eine Shell im Kontext Ihrer Anwendung, damit Sie Ihre Modelle bearbeiten können.

    ![Konsole](media/template-django-console-shell.png)

- **Django-DB synchronisieren**: Führt `manage.py syncdb` in einem interaktiven Fenster aus:

    ![Konsole](media/template-django-console-sync-db.png)

- **Statische erfassen**: Führt `manage.py collectstatic --noinput` aus, um alle statischen Dateien in den durch `STATIC_ROOT` angegebenen Pfad in Ihrer `settings.py` zu kopieren. Hinweis: Bei der [Veröffentlichung in Microsoft Azure](template-web.md#publishing-to-azure-app-service) werden statische Dateien automatisch als Teil des Veröffentlichungsvorgangs gesammelt.

    ![Konsole](media/template-django-console-collect-static.png)

- **Überprüfen**: Führt `manage.py validate` aus, wodurch Überprüfungsfehler in den installierten Modellen gemeldet werden, die durch `INSTALLED_APPS` in Ihrer `settings.py` angegeben wurden:

    ![Konsole](media/template-django-console-validate.png)
