---
title: "Webprojektvorlage in Python-Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 401e7725-8be5-4e67-862c-bf0690a529e3
caps.latest.revision: 11
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
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 2375c0c3b1a692d03d8790e400e3fea606355831
ms.lasthandoff: 03/10/2017

---

# <a name="python-web-project-templates"></a>Python-Webprojektvorlagen

Python-Tools für Visual Studio (PTVS) umfassen Unterstützung für die Entwicklung von Webprojekten in Frameworks wie Bottle, Django und Flask. Hierzu gehören Projektvorlagen und ein Debugstartprogramm, das für die Verarbeitung verschiedener Frameworks konfiguriert werden kann. PTVS enthält jedoch nicht die Frameworks selbst. Diese müssen Sie getrennt installieren, indem Sie mit der rechten Maustaste auf das Projekt klicken und **Python > Framework installieren/aktualisieren** wählen.

Jede Vorlage (zugänglich über **Datei > Neu > Projekt**) startet einen Webserver mit einem zufällig ausgewählten lokalen Port, öffnen Ihren Standardbrowser beim Debuggen und ermöglicht eine direkte Veröffentlichung in [Microsoft Azure](http://www.azure.com). Vorlagen werden für Bottle, Flask und Django bereitgestellt und können Sie die generische Vorlage „Webprojekt“ für andere Frameworks wie Pyramid nutzen.

![Neue Webprojektvorlagen](media/template-web-new-project.png)

Die Vorlagen für Bottle, Flask und Django enthalten jeweils eine Startwebsite mit einigen Seiten und statischen Dateien. Dieser Code ist ausreichend für das lokale Ausführen und Debuggen des Servers (wobei einige Einstellungen aus der Umgebung abgerufen werden müssen) sowie für das Bereitstellen für Microsoft Azure (wobei ein [WSGI-App](http://www.python.org/dev/peps/pep-3333/)-Objekt angegeben werden muss).

Beim Erstellen eines Projekts mit einer frameworkspezifischen Vorlage wird ein Dialogfeld angezeigt, das Sie bei der Installation der erforderlichen Pakete über PIP unterstützt. Zudem empfehlen wir die Verwendung einer [virtuellen Umgebung](python-environments.md#virtual-environments) für Webprojekte, damit beim Veröffentlichen der Website die richtigen Abhängigkeiten enthalten sind:

![Dialogfeld, über das die erforderlichen Pakete für eine Projektvorlage installiert werden](media/template-web-requirements-txt-wizard.png)

Bei der Bereitstellung in Microsoft Azure App Service müssen Sie eine Version von Python als [Websiteerweiterung](https://aka.ms/PythonOnAppService) auswählen und Pakete manuell installieren. Da Pakete in Azure App Service bei Bereitstellung über Visual Studio **nicht** automatisch anhand einer `requirements.txt`-Datei installiert werden, befolgen Sie außerdem die Konfigurationsdetails unter [aka.ms/PythonOnAppService](https://aka.ms/PythonOnAppService).

In Microsoft Azure Cloud Services wird die `requirements.txt`-Datei hingegen unterstützt. Weitere Details finden Sie unter [Azure Cloud Services-Projekte](template-azure-cloud-service.md).

Eine Einführung in Python-Webprojekte finden Sie in diesem Video: [Getting Started with PTVS, Part 6: Web sites](https://youtu.be/FJx5mutt1uk?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (youtube.com, 3 Minuten, 10 Sekunden).

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk]

## <a name="debugging"></a>Debuggen

Wenn ein Webprojekt für das Debuggen gestartet wird, startet PTVS den Webserver lokal und öffnet Ihren Standardbrowser mit dieser Adresse und diesem Port. Um zusätzliche Optionen anzugeben, klicken Sie mit der rechten Maustaste auf das Projekt, wählen Sie **Eigenschaften**, und wählen Sie die Registerkarte **Webstartprogramm**:

  ![Eigenschaften des Webstartprogramms für die generische Webvorlage](media/template-web-launcher-properties.png)

Gruppe **Debuggen**:

- **Suchpfade**, **Skriptargumente**, **Interpreterargumente** und **Interpreterpfad**: Diese Optionen stimmen mit denen für das [normale Debuggen](debugging.md) überein.
- **Start-URL**: Gibt die URL an, die in Ihrem Browser geöffnet wird. Sie wird standardmäßig auf `localhost` festgelegt.
- **Portnummer**: Gibt den Port an, der verwendet wird, wenn in der URL keiner angegeben ist. (Standardmäßig wird er von PTVS automatisch ausgewählt.) Dadurch können Sie den Standardwert der `SERVER_PORT`-Umgebungsvariablen außer Kraft setzen, der von den Vorlagen zur Konfiguration des Ports verwendet wird, auf den der lokale Debugserver lauscht.

Durch die Eigenschaften in den Gruppen **Serverbefehl ausführen** und **Debugserverbefehl** (letzterer befindet sich weiter unten und wird in der Abbildung nicht gezeigt) wird festgelegt, wie der Webserver gestartet wird. Da für viele Frameworks die Verwendung eines Skripts außerhalb des aktuellen Projekts erforderlich ist, kann das Skript hier konfiguriert und der Name des Startmoduls als Parameter übergeben werden.

- **Befehl**: Hierbei kann es sich um ein Python-Skript (`*.py`-Datei), einen Modulnamen (wie in `python.exe -m module_name`) oder eine einzelne Codezeile (wie in `python.exe -c "code"`) handeln. Der Wert in der Dropdownliste gibt an, welcher dieser Typen vorgesehen ist.
- **Argumente**: Diese werden in der Befehlszeile nach dem Befehl übergeben.
- **Umgebung**: eine durch Zeilenumbrüche getrennte Liste von `NAME=VALUE`-Paaren, durch die die Umgebungsvariablen angegeben werden. Diese werden nach allen Eigenschaften festgelegt, durch die die Umgebung möglicherweise geändert wird (z.B. Portnummer und Suchpfade), und können daher diese Werte überschreiben.

Jede Projekteigenschaft oder Umgebungsvariable kann mit der MSBuild-Syntax angegeben werden. Beispiel: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` ist der relative Pfad zur Startdatei, und `{StartupModule}` ist der importierbare Name der Startdatei. `$(SERVER_HOST)` und `$(SERVER_PORT)` sind normale Umgebungsvariablen, die durch die Eigenschaften **Start-URL** und **Portnummer**, automatisch oder durch die Eigenschaft **Umgebung** festgelegt werden.

> [!Note]
> Werte unter **Serverbefehl ausführen** werden mit dem Befehl **Debuggen > Server starten** oder STRG+F5 verwendet. Werte in der Gruppe **Debugserverbefehl** werden mit dem Befehl **Debuggen > Debugserver starten** oder F5 verwendet.


### <a name="sample-bottle-configuration"></a>Beispiel für eine Bottle-Konfiguration

Die Bottle-Webprojektvorlage enthält Codebausteine, die die erforderliche Konfiguration vornehmen. Eine importierte Bottle-App enthält diesen Code jedoch möglicherweise nicht. In diesem Fall wird die App durch die folgenden Einstellungen über das installierte `bottle`-Modul gestartet:

- Gruppe **Serverbefehl ausführen**:
    - **Befehl**: `bottle` (Modul)
    - **Argumente**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Gruppe **Debugserverbefehl**:
    - **Befehl**: `bottle` (Modul)
    - **Argumente**: `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

Die `--reload`-Option wird nicht empfohlen, wenn Sie PTVS für das Debuggen verwenden.

### <a name="sample-pyramid-configuration"></a>Beispiel für eine Pyramid-Konfiguration

Pyramid-Apps werden derzeit am besten über das `pcreate`-Befehlszeilentool erstellt. Nachdem eine App erstellt wurde, kann sie mithilfe der Vorlage [Aus vorhandenem Python-Code](python-projects.md#creating-a-project-from-existing-files) importiert werden. Wählen Sie danach die Anpassung **Generisches Webprojekt**, um die Optionen zu konfigurieren. Bei diesen Einstellungen wird davon ausgegangen, dass Pyramid in einer virtuellen Umgebung unter `..\env` installiert ist.

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

Zum Installieren von Python in App Service empfehlen wir die Verwendung der [Websiteerweiterungen](http://www.siteextensions.net/packages?q=Tags%3A%22python%22) (siteextensions.net). Hierbei handelt es sich um eine Kopie der [offiziellen Releases](https://www.python.org) von Python, die für Azure App Service optimiert und neu zusammengestellt wurden.

Eine Websiteerweiterung kann im [Azure-Portal](https://portal.azure.com/) über das Blatt **Entwicklungstools > Erweiterungen** für App Service bereitgestellt werden, indem Sie **Hinzufügen** auswählen und die Liste nach den Erweiterungen für Python durchsuchen:

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

```
c:\Python35\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt

c:\Python27\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt
```

Bei Bereitstellung in Azure App Service wird Ihre Website hinter Microsoft IIS ausgeführt. Um die Zusammenarbeit Ihrer Website mit IIS zu ermöglichen, müssen Sie mindestens eine `web.config`-Datei hinzufügen. Für einige gängige Bereitstellungsziele stehen Vorlagen zur Verfügung, die Sie durch Klicken mit der rechten Maustaste auf das Projekt und durch Auswahl von „Hinzufügen“ > „Neues Element“ (wie im folgenden Dialogfeld gezeigt) aufrufen können. Diese können problemlos für andere Zwecke geändert werden. Informationen zu den verfügbaren Konfigurationseinstellungen finden Sie in der [Referenz zur IIS-Konfiguration](https://www.iis.net/configreference).

![Azure-Elementvorlagen](media/template-web-azure-items.png)

Die folgenden Elemente sind verfügbar:

- „web.config“ für Azure (FastCGI): Fügt eine `web.config`-Datei hinzu, wenn Ihre App ein [WSGI](https://wsgi.readthedocs.io/en/latest/)-Objekt zum Behandeln eingehender Verbindungen bereitstellt.
- „web.config“ für Azure (HttpPlatformHandler): Fügt eine `web.config`-Datei hinzu, wenn Ihre App auf einen Socket für eingehende Verbindungen lauscht.
- „web.config“ für statische Azure-Dateien: Wenn Sie eine der oben genannten `web.config`-Dateien verwenden, fügen Sie diese einem Unterverzeichnis hinzu, um sie von der Verarbeitung durch Ihre App auszuschließen.
- „web.config“ für das Remotedebuggen in Azure: Fügt die Dateien hinzu, die für das Remotedebuggen über WebSockets erforderlich sind.
- Webrollen-Unterstützungsdateien: Enthält die Standardbereitstellungsskripts für Cloud Services-Webrollen.
- Workerrollen-Unterstützungsdateien: Enthält die Standardbereitstellungsskripts und Startskripts für Cloud Services-Workerrollen.

Wenn Sie Ihrem Projekt die `web.config`-Debuggingvorlage hinzufügen und das Remotedebuggen in Python verwenden möchten, müssen Sie die Website in der Konfiguration „Debug“ veröffentlichen. Diese Einstellung ist von der aktuellen aktiven Konfiguration der Projektmappe getrennt und lautet standardmäßig „Release“. Um sie zu ändern, öffnen Sie die Registerkarte **Einstellungen**, und verwenden Sie das Kombinationsfeld **Konfiguration** im Veröffentlichungs-Assistenten (weitere Informationen zur Erstellung und Bereitstellung in Azure-Web-Apps finden Sie in der [Azure-Dokumentation](https://azure.microsoft.com/develop/python/)):

![Ändern der Veröffentlichungskonfiguration](media/template-web-publish-config.png)

Mit dem Befehl **In Microsoft Azure Cloud Services-Projekt konvertieren** (Abbildung unten) wird Ihrer Projektmappe ein Cloud Services-Projekt hinzugefügt. Dieses Projekt umfasst die Bereitstellungseinstellungen und die Konfiguration für die zu verwendenden virtuellen Computer und Dienste. Verwenden Sie den Befehl **Veröffentlichen** im Cloudprojekt zur Bereitstellung in Cloud Services; mit dem Befehl **Veröffentlichen** im Python-Projekt erfolgt die Bereitstellung weiterhin auf Websites. Weitere Details finden Sie unter [Azure Cloud Services-Projekte](template-azure-cloud-service.md).

![Befehl „In Microsoft Azure Cloud Services-Projekt konvertieren“](media/template-web-convert-menu.png)

