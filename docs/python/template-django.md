---
title: "Django-Webprojektvorlage in Python-Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c479be58-13eb-4d77-9a27-c97ddc290963
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 7f65641fbf15edfe16931badc19602a0fc773bff
ms.lasthandoff: 03/07/2017

---

# <a name="django-web-project-template"></a>Django-Webprojektvorlage

[Django](https://www.djangoproject.com/) ist ein allgemeines Python-Framework für die schnelle, sichere und skalierbare Webentwicklung. Python-Tools für Visual Studio (PTVS) enthält eine Projektvorlage zum Einrichten der Struktur einer Django-basierten Webanwendung. Um die Vorlage in Visual Studio zu verwenden, wählen Sie **Datei > Neu > Projekt**, suchen Sie nach „Django“, und wählen Sie die Vorlage „Django-Webprojekt“ aus. Das resultierende Projekt umfasst Codebausteine sowie eine SQLite-Standarddatenbank. Die Vorlage „Leeres Django-Webprojekt“ ist ähnlich, enthält jedoch nicht die Datenbank.

PTVS bietet vollständiges IntelliSense für Django-Projekte:

- An die Vorlage übergebene Kontextvariablen:

    ![IntelliSense für Kontextvariablen](media/template-django-intellisense.png)

- Markierungen und Filter sowohl für integrierte als auch für benutzerdefinierte Variablen:

    ![IntelliSense für Tags und Filter](media/template-django-intellisense-filter.png)

- Syntaxfarben für eingebettetes CSS und JavaScript:

    ![CSS-IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)


PTVS bietet außerdem vollständige [Debuggingunterstützung](debugging.md) für Django-Projekte: 

![Haltepunkte](media/template-django-debugging.png)

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
