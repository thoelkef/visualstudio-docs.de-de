---
title: "Webanwendungsvorlagen für Python in Visual Studio | Microsoft-Dokumentation"
description: "Eine Übersicht der Visual Studio-Vorlagen für in Python mithilfe der Bottle-, Flask- und Django-Frameworks erstellte Webanwendungen, einschließlich Debugkonfigurationen und Veröffentlichung im Azure App Service."
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: b9cc38b30e078ed716d9f0c590796d19ed50c883
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="python-web-application-project-templates"></a>Projektvorlagen für Python-Webanwendungen

Python in Visual Studio unterstützt das Entwickeln von Webprojekten in Bottle-, Flask- und Django-Frameworks mit Projektvorlagen und einem Debugstartprogramm, das so konfiguriert werden kann, dass es mehrere Frameworks behandeln kann. Sie können auch die generische Vorlage **Webprojekt** für andere Frameworks wie z.B Pyramid verwenden.

Diese Frameworks sind nicht in Visual Studio enthalten. Sie müssen Frameworks separat installieren, indem Sie mit der rechten Maustaste auf das Projekt klicken und **Python > Framework installieren/aktualisieren** auswählen.

Wenn ein Projekt, das mithilfe einer Vorlage (zugänglich über **Datei > Neu > Projekt**) erstellt wurde, ausgeführt wird, wird ein Webserver mit einem zufällig ausgewählten lokalen Port gestartet, Ihr Standardbrowser beim Debuggen geöffnet, und die direkte Veröffentlichung in Microsoft Azure wird ermöglicht.

![Neue Webprojektvorlagen](media/template-web-new-project.png)

Die Vorlagen für Bottle, Flask und Django enthalten jeweils eine Startwebsite mit einigen Seiten und statischen Dateien. Dieser Code ist ausreichend für das lokale Ausführen und Debuggen des Servers (wobei einige Einstellungen aus der Umgebung abgerufen werden müssen) sowie für das Bereitstellen für Microsoft Azure (wobei ein [WSGI-App](http://www.python.org/dev/peps/pep-3333/)-Objekt angegeben werden muss).

Wenn Sie ein Projekt über eine frameworkspezifische Vorlage erstellen, wird ein Dialogfeld angezeigt, das Ihnen bei der Installation der erforderlichen Pakete mit pip hilft. Zudem empfehlen wir die Verwendung einer [virtuellen Umgebung](managing-python-environments-in-visual-studio.md#global-and-virtual-environments) für Webprojekte, damit beim Veröffentlichen der Website die richtigen Abhängigkeiten enthalten sind:

![Dialogfeld, über das die erforderlichen Pakete für eine Projektvorlage installiert werden](media/template-web-requirements-txt-wizard.png)

Wählen Sie bei der Bereitstellung in Microsoft Azure App Service eine Version von Python als [Websiteerweiterung](https://aka.ms/PythonOnAppService), und installieren Sie Pakete manuell. Da Pakete in Azure App Service bei Bereitstellung über Visual Studio **nicht** automatisch anhand einer `requirements.txt`-Datei installiert werden, befolgen Sie außerdem die Konfigurationsdetails unter [aka.ms/PythonOnAppService](https://aka.ms/PythonOnAppService).

Die `requirements.txt`-Datei hingegen wird in Microsoft Azure Cloud Services *unterstützt*. Weitere Informationen finden Sie unter [Projekte für Azure-Clouddienste für Python](python-azure-cloud-service-project-template.md).

## <a name="debugging"></a>Debuggen

Wenn ein Webprojekt zum Debuggen gestartet wird, startet Visual Studio den Webserver lokal und öffnet Ihren Standardbrowser mit dieser Adresse und diesem Port. Um zusätzliche Optionen anzugeben, klicken Sie mit der rechten Maustaste auf das Projekt, wählen Sie **Eigenschaften** aus, und wählen Sie dann die Registerkarte **Webstartprogramm** aus:

  ![Eigenschaften des Webstartprogramms für die generische Webvorlage](media/template-web-launcher-properties.png)

Gruppe **Debuggen**:

- **Suchpfade**, **Skriptargumente**, **Interpreterargumente** und **Interpreterpfad**: Diese Optionen stimmen mit denen für das [normale Debuggen](debugging-python-in-visual-studio.md) überein.
- **Start-URL**: Gibt die URL an, die in Ihrem Browser geöffnet wird. Sie wird standardmäßig auf `localhost` festgelegt.
- **Portnummer**: Gibt den Port an, der verwendet wird, wenn in der URL keiner angegeben ist. (Standardmäßig wird er von Visual Studio automatisch ausgewählt.) Durch diese Eigenschaft können Sie den Standardwert der `SERVER_PORT`-Umgebungsvariablen außer Kraft setzen, der von den Vorlagen zur Konfiguration des Ports verwendet wird, auf den der lokale Debugserver lauscht.

Durch die Eigenschaften in den Gruppen **Serverbefehl ausführen** und **Debugserverbefehl** (letzterer befindet sich weiter unten und wird in der Abbildung nicht gezeigt) wird festgelegt, wie der Webserver gestartet wird. Da für viele Frameworks die Verwendung eines Skripts außerhalb des aktuellen Projekts erforderlich ist, kann das Skript hier konfiguriert und der Name des Startmoduls als Parameter übergeben werden.

- **Befehl**: Hierbei kann es sich um ein Python-Skript (`*.py`-Datei), einen Modulnamen (wie in `python.exe -m module_name`) oder eine einzelne Codezeile (wie in `python.exe -c "code"`) handeln. Der Wert in der Dropdownliste gibt an, welcher dieser Typen beabsichtigt ist.
- **Argumente**: Diese Argumente werden in der Befehlszeile nach dem Befehl übergeben.
- **Umgebung**: eine durch Zeilenumbrüche getrennte Liste von `NAME=VALUE`-Paaren, durch die die Umgebungsvariablen angegeben werden. Diese Variablen werden nach allen Eigenschaften festgelegt, durch die die Umgebung möglicherweise modifiziert wird (z.B. Portnummer und Suchpfade), und können daher diese Werte überschreiben.

Jede Projekteigenschaft oder Umgebungsvariable kann mit der MSBuild-Syntax angegeben werden. Beispiel: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` ist der relative Pfad zur Startdatei, und `{StartupModule}` ist der importierbare Name der Startdatei. `$(SERVER_HOST)` und `$(SERVER_PORT)` sind normale Umgebungsvariablen, die durch die Eigenschaften **Start-URL** und **Portnummer**, automatisch oder durch die Eigenschaft **Umgebung** festgelegt werden.

> [!Note]
> Werte unter **Serverbefehl ausführen** werden mit dem Befehl **Debuggen > Server starten** oder STRG+F5 verwendet. Werte in der Gruppe **Debugserverbefehl** werden mit dem Befehl **Debuggen > Debugserver starten** oder F5 verwendet.

### <a name="sample-bottle-configuration"></a>Beispiel für eine Bottle-Konfiguration

Die Vorlage **Bottle-Webprojekt** enthält Codebausteine, die die erforderliche Konfiguration vornehmen. Eine importierte Bottle-App enthält diesen Code jedoch möglicherweise nicht. In diesem Fall wird die App durch die folgenden Einstellungen über das installierte `bottle`-Modul gestartet:

- Gruppe **Serverbefehl ausführen**:
  - **Befehl**: `bottle` (Modul)
  - **Argumente**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Gruppe **Debugserverbefehl**:
  - **Befehl**: `bottle` (Modul)
  - **Argumente**: `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

Die `--reload`-Option wird nicht empfohlen, wenn Sie Visual Studio für das Debuggen verwenden.

### <a name="sample-pyramid-configuration"></a>Beispiel für eine Pyramid-Konfiguration

Pyramid-Apps werden derzeit am besten über das `pcreate`-Befehlszeilentool erstellt. Nachdem eine App erstellt wurde, kann sie mithilfe der Vorlage [Aus vorhandenem Python-Code](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files) importiert werden. Wählen Sie danach die Anpassung **Generisches Webprojekt**, um die Optionen zu konfigurieren. Bei diesen Einstellungen wird davon ausgegangen, dass Pyramid in einer virtuellen Umgebung unter `..\env` installiert ist.

- Gruppe **Debuggen**:
  - **Serverport**: 6543 (bzw. entsprechend der Konfiguration in den INI-Dateien)

- Gruppe **Serverbefehl ausführen**:
  - Befehl: `..\env\scripts\pserve-script.py` (Skript)
  - Argumente: `Production.ini`

- Gruppe **Debugserverbefehl**:
    - Befehl: `..\env\scripts\pserve-script.py` (Skript)
    - Argumente: `Development.ini`

> [!Tip]
> Sie müssen wahrscheinlich die Eigenschaft **Arbeitsverzeichnis** Ihres Projekts konfigurieren, weil Pyramid-Apps sich in der Regel eine Verzeichnisebene unterhalb der Spitze der Quellstruktur befinden.

### <a name="other-configurations"></a>Weitere Konfigurationen

Wenn Sie Einstellungen für ein anderes Framework verwenden, die Sie teilen möchten, oder wenn Sie Einstellungen für ein anderes Framework anfordern möchten, öffnen Sie ein [Problem in GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="publishing-to-azure-app-service"></a>Veröffentlichen in Azure App Service

Es gibt im Wesentlichen zwei Methoden für die Veröffentlichung in Azure App Service. Als Erstes kann die Bereitstellung über die Quellcodeverwaltung auf die gleiche Weise wie bei anderen Sprachen verwendet werden, wie beschrieben in der [Azure-Dokumentation](http://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/). Zur direkten Veröffentlichung aus Visual Studio klicken Sie mit der rechten Maustaste auf das Projekt und wählen **Veröffentlichen**:

![Befehl „Veröffentlichen“ im Kontextmenü eines Projekts](media/template-web-publish-command.png)

Nach Auswahl des Befehls werden Sie von einem Assistenten durch das Erstellen einer Website oder das Importieren von Veröffentlichungseinstellungen, das Anzeigen einer Vorschau der geänderten Dateien und das Veröffentlichen auf einem Remoteserver geleitet.

Wenn Sie eine Website in App Service erstellen, müssen Sie Python und alle Pakete installieren, von denen Ihre Website abhängig ist. Sie können zwar zuerst Ihre Website veröffentlichen, aber sie wird erst ausgeführt, wenn Sie Python konfiguriert haben.

Zum Installieren von Python in App Service empfehlen wir die Verwendung der [Websiteerweiterungen](http://www.siteextensions.net/packages?q=Tags%3A%22python%22) (siteextensions.net). Bei diesen Erweiterungen handelt es sich um Kopien der [offiziellen Releases](https://www.python.org) von Python, die für Azure App Service optimiert und neu zusammengestellt wurden.

Sie können eine Websiteerweiterung über das [Azure-Portal](https://portal.azure.com/) bereitstellen. Klicken Sie auf das Blatt **Entwicklungstools** für Ihren App Service, klicken Sie auf **Hinzufügen**, und scrollen Sie durch die Liste, um die Python-Elemente zu suchen:

![Hinzufügen einer Websiteerweiterung im Azure-Portal](media/template-web-site-extensions.png)

Wenn Sie JSON-Bereitstellungsvorlagen verwenden, können Sie die Websiteerweiterung als Ressource Ihrer Website angeben:

```json
{
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "[parameters('siteName')]",
        "type": "Microsoft.Web/sites",
        ...
    },
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "python352x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
    },
    ...
}
```

Schließlich können Sie sich über die [Entwicklungskonsole](https://github.com/projectkudu/kudu/wiki/Kudu-console) anmelden und von dort aus eine Websiteerweiterung installieren.

Derzeit besteht die empfohlene Methode zur Installation von Paketen darin, die Entwicklungskonsole zu verwenden, nachdem die Websiteerweiterung installiert und PIP direkt ausgeführt wurde. Der vollständige Pfad zu Python muss unbedingt verwendet werden, da Sie ansonsten möglicherweise die falsche Version ausführen. Die Verwendung einer virtuellen Umgebung ist im Allgemeinen nicht erforderlich. Zum Beispiel:

```command
c:\Python35\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt

c:\Python27\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt
```

Bei Bereitstellung in Azure App Service wird Ihre Website hinter Microsoft IIS ausgeführt. Um die Zusammenarbeit Ihrer Website mit IIS zu ermöglichen, müssen Sie mindestens eine `web.config`-Datei hinzufügen. Für einige gängige Bereitstellungsziele stehen Vorlagen zur Verfügung, die Sie durch Klicken mit der rechten Maustaste auf das Projekt und durch Auswahl von **Hinzufügen > Neues Element** (wie im folgenden Dialogfeld gezeigt) aufrufen können. Diese Konfigurationen können problemlos für andere Zwecke geändert werden. Informationen zu den verfügbaren Konfigurationseinstellungen finden Sie in der [Referenz zur IIS-Konfiguration](https://www.iis.net/configreference).

![Azure-Elementvorlagen](media/template-web-azure-items.png)

Die folgenden Elemente sind verfügbar:

- „web.config“ für Azure (FastCGI): Fügt eine `web.config`-Datei hinzu, wenn Ihre App ein [WSGI](https://wsgi.readthedocs.io/en/latest/)-Objekt zum Behandeln eingehender Verbindungen bereitstellt.
- „web.config“ für Azure (HttpPlatformHandler): Fügt eine `web.config`-Datei hinzu, wenn Ihre App auf einen Socket für eingehende Verbindungen lauscht.
- „web.config“ für statische Azure-Dateien: Wenn Sie eine der oben genannten `web.config`-Dateien verwenden, fügen Sie diese einem Unterverzeichnis hinzu, um sie von der Verarbeitung durch Ihre App auszuschließen.
- „web.config“ für das Remotedebuggen in Azure: Fügt die Dateien hinzu, die für das Remotedebuggen über WebSockets erforderlich sind.
- Webrollen-Unterstützungsdateien: Enthält die Standardbereitstellungsskripts für Webrollen in Clouddiensten.
- Workerrollen-Unterstützungsdateien: Enthält die Standardbereitstellungsskripts und Startskripts für Workerrollen in Clouddiensten.

Wenn Sie Ihrem Projekt die `web.config`-Debuggingvorlage hinzufügen und das Remotedebuggen in Python verwenden möchten, müssen Sie die Website in der Konfiguration „Debug“ veröffentlichen. Diese Einstellung ist von der aktuellen aktiven Konfiguration der Projektmappe getrennt und lautet standardmäßig „Release“. Um sie zu ändern, öffnen Sie die Registerkarte **Einstellungen**, und verwenden Sie das Kombinationsfeld **Konfiguration** im Veröffentlichungs-Assistenten (weitere Informationen zur Erstellung und Bereitstellung in Azure-Web-Apps finden Sie in der [Azure-Dokumentation](https://azure.microsoft.com/develop/python/)):

![Ändern der Veröffentlichungskonfiguration](media/template-web-publish-config.png)

Mit dem Befehl **In Microsoft Azure Cloud Services-Projekt konvertieren** (Abbildung unten) wird Ihrer Projektmappe ein Clouddienst-Projekt hinzugefügt. Dieses Projekt umfasst die Bereitstellungseinstellungen und die Konfiguration für die zu verwendenden virtuellen Computer und Dienste. Verwenden Sie den Befehl **Veröffentlichen** im Cloudprojekt zur Bereitstellung in Cloud Services. Mit dem Befehl **Veröffentlichen** im Python-Projekt erfolgt die Bereitstellung weiterhin auf Websites. Weitere Informationen finden Sie unter [Projekte für Azure-Clouddienste für Python](python-azure-cloud-service-project-template.md).

![Befehl „In Microsoft Azure Cloud Services-Projekt konvertieren“](media/template-web-convert-menu.png)
