---
title: Elementvorlagen für Python-Projekte
description: Eine Referenzliste von Elementvorlagen für Python-Projekte, die über Hinzufügen > Neues Element in Visual Studio verfügbar sind.
ms.date: 09/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 8319c99e5de12ce1c09a2c20fc5cf1b132f34092
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776034"
---
# <a name="python-item-templates"></a>Python-Elementvorlagen

Die Elementvorlagen sind in Python-Projekten über den Menübefehl **Projekt** > **Neues Element hinzufügen** oder den Befehl **Hinzufügen** > **Neues Element** im Kontextmenü in **Projektmappen-Explorer** verfügbar.

![Dialogfeld "Neues Element hinzufügen"](media/project-item-templates.png)

Eine Vorlage erstellt mithilfe des Namens, den Sie für das Element angeben, normalerweise mindestens eine Datei und mindestens einen Ordner in dem aktuell ausgewählten Ordner im Projekt (wenn Sie mit der rechten Maustaste auf einen Ordner klicken, um das Kontextmenü aufzurufen, wird der Ordner automatisch ausgewählt). Wenn ein Element hinzugefügt wird, wird es in das Visual Studio-Projekt eingeschlossen, und das Element wird im **Projektmappen-Explorer** angezeigt.

Die folgende Tabelle erklärt kurz die Auswirkung jeder Elementvorlage in einem Python-Projekt:

| Vorlage | Die Vorlage erstellt |
| --- | --- |
| **Leere Python-Datei** | Leere Datei mit der Erweiterung *.py*. |
| **Python-Klasse** | *.py*-Datei, die eine leere Python-Klassendefinition enthält. |
| **Python-Paket** | Ein Ordner, der eine *\_\_init\_\_.py*-Datei enthält. |
| **Python-Komponententest** | Eine *.py*-Datei mit einem Komponententest, der auf dem `unittest`-Framework basiert, sowie Aufruf von `unittest.main()`, um die Tests in der Datei auszuführen. |
| **HTML-Seite** | *.html*-Datei mit einer einfachen Seitenstruktur, die aus einem `<head>`- und einem `<body>`-Element besteht. |
| **JavaScript** | Eine leere *.js*-Datei. |
| **Stylesheet** | Eine *.css*-Datei, die eine leere Formatvorlage für `body` enthält. |
| **Textdatei** | Eine leere *.txt*-Datei. |
| **Django 1.9-App**<br/>**Django 1.4-App** | Ordner mit dem Namen der App, der die Core-Dateien für eine Django-App enthält, wie in [Informationen zu Django in Visual Studio – Schritt 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) für Django 1.9 erläutert. Für Django 1.4 sind der Ordner *migrations*, die Datei *admin.py* und die Datei *apps.py* nicht enthalten. |
| **IronPython-WPF-Fenster** | Ein WPF-Fenster, das aus zwei parallelen Dateien besteht: einer *.xaml*-Datei, die ein `<Window>` mit einem leeren `<Grid>`-Element definiert, und einer verknüpften *.py*-Datei, die die XAML-Datei mithilfe der `wpf`-Bibliothek lädt. Wird normalerweise in einem Projekt verwendet, das mit einer der IronPython-Vorlagen erstellt wurde. Weitere Informationen finden Sie unter [Verwalten von Python-Projekten – Projektvorlagen](managing-python-projects-in-visual-studio.md#project-templates). |
| **Webrollen-Unterstützungsdateien** | Ein *bin*-Ordner im Projektstammverzeichnis (unabhängig vom ausgewählten Ordner im Projekt). Der Ordner enthält ein Standardbereitstellungsskript und eine *web.config*-Datei für Azure-Clouddienstwebrollen. Die Vorlage enthält auch eine *readme.html*-Datei, die die Details erläutert. |
| **Unterstützungsdateien für Workerrollen** | Ein *bin*-Ordner im Projektstammverzeichnis (unabhängig vom ausgewählten Ordner im Projekt). Der Ordner enthält ein Standardbereitstellungs- und Startskript sowie eine *web.config*-Datei für Workerrollen in Azure-Clouddiensten. Die Vorlage enthält auch eine *readme.html*-Datei, die die Details erläutert. |
| **„web.config“ für Azure (FastCGI)** | *web.config*-Datei, die Einträge für Apps enthält, die mit einem [WSGI](https://wsgi.readthedocs.io/en/latest/)-Objekt eingehende Verbindungen verarbeiten. Diese Datei wird in der Regel in das Stammverzeichnis eines Webservers bereitgestellt, auf dem IIS ausgeführt wird, z.B. Azure App Service. Weitere Informationen finden Sie unter [Veröffentlichen in Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| **„web.config“ für Azure (HttpPlatformHandler)** | *web.config*-Datei, die Einträge für die Apps enthält, die an einem Socket für eingehende Verbindungen lauschen. Diese Datei wird in der Regel in das Stammverzeichnis eines Webservers bereitgestellt, auf dem IIS ausgeführt wird, z.B. Azure App Service. Weitere Informationen finden Sie unter [Veröffentlichen in Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| **„web.config“ für statische Azure-Dateien** | -*web.config*Datei, die in der Regel einem *static*-Ordner (oder einem anderen Ordner, der statische Elemente enthält) hinzugefügt wird, um die Python-Verarbeitung für diesen Ordner zu deaktivieren. Diese Konfigurationsdatei funktioniert in Verbindung mit einer der oben genannten FastCGI- oder HttpPlatformHandler-Konfigurationsdateien. Weitere Informationen finden Sie unter [Veröffentlichen in Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| **„web.config“ für das Remotedebuggen in Azure** | *web.config.debug*-Datei, die das Remotedebuggen über WebSockets aktiviert, sowie die Datei *Microsoft.PythonTools.WebRole.dll* und ein *ptvsd*-Ordner mit den Modulen zum Bereitstellen für den Server, um das Remotedebuggen zu aktivieren. Sie erstellen dieses Element in der Regel am gleichen Ort wie Ihre *web.config*-Datei. Weitere Informationen finden Sie unter [Remotedebuggen von Python-Code in Azure](debugging-remote-python-code-on-azure.md). Lesen Sie außerdem den folgenden Hinweis. |

> [!Note]
> Wenn Sie einem Projekt die *web.config*-Debuggingvorlage hinzufügen und das Remotedebuggen in Python verwenden möchten, müssen Sie die Website in der Konfiguration **Debug** veröffentlichen. Diese Einstellung ist von der aktuellen aktiven Konfiguration der Projektmappe getrennt und lautet standardmäßig **Release**. Um dies zu ändern, öffnen Sie die Registerkarte **Einstellungen**, und verwenden Sie das Kombinationsfeld **Konfiguration** im **Veröffentlichungs-Assistenten**. (Weitere Informationen zum Erstellen und Bereitstellen an Azure-Web-Apps finden Sie in der [Azure-Dokumentation](https://azure.microsoft.com/develop/python/).)
>
> ![Ändern der Veröffentlichungskonfiguration](media/template-web-publish-config.png)

## <a name="see-also"></a>Siehe auch

- [Verwalten von Python-Projekten – Projektvorlagen](managing-python-projects-in-visual-studio.md#project-templates)
- [Python-Webprojektvorlagen](python-web-application-project-templates.md)
- [Veröffentlichen in Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
