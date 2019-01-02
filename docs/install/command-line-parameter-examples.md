---
title: Beispiele für Befehlszeilenparameter für die Installation
description: Passen Sie diese Beispiele an, um Ihre eigene Installation von Visual Studio über die Befehlszeile zu erstellen.
ms.date: 11/14/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a1a0d0af09768e4927403d0791ae4c1e7785dcb
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53562171"
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Beispiele für die Befehlszeilenparameter für die Installation von Visual Studio 2017

Zur Veranschaulichung, wie [Befehlszeilenparameter zur Installation von Visual Studio](use-command-line-parameters-to-install-visual-studio.md) verwendet werden, sind hier einige Beispiele aufgeführt, die sie Ihren Bedürfnissen anpassen können.

In jedem Beispiel stellen `vs_enterprise.exe`, `vs_professional.exe` und `vs_community.exe` die jeweilige Edition des Visual Studio-Bootstrappers dar, was die kleine Datei ist (ca. 1 MB), die den Downloadprozess initiiert. Wenn Sie eine andere Edition verwenden, ersetzen Sie die entsprechenden Bootstrappernamen.

> [!NOTE]
> Alle Befehle erfordern administrative Erhöhung, und ein Befehl der Benutzerkontensteuerung wird angezeigt, wenn der Prozess nicht von einer erhöhten Aufforderung gestartet wurde.
>
> [!NOTE]
>  Sie können die `^`-Zeichen am Ende einer Befehlszeile zum Verketten mehrerer Zeilen in einem einzigen Befehl verwenden. Alternativ können Sie einfach diese Zeilen zusammen in einer einzelnen Zeile platzieren. Die Entsprechung in PowerShell ist das Graviszeichen (`` ` ``).

## <a name="using---installpath"></a>Verwenden von „--installPath“

* Installieren Sie eine minimale Instanz von Visual Studio ohne interaktive Anweisungen, aber mit angezeigtem Status:

  ```cmd
  vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Aktualisieren Sie mithilfe der Befehlszeile eine Visual Studio-Instanz ohne interaktive Eingabeaufforderungen, aber mit angezeigtem Status:

  ```cmd
  vs_enterprise.exe --update --quiet --wait
  vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
  ```

  > [!NOTE]
  > Beide Befehle sind erforderlich. Mit dem ersten Befehl wird der Visual Studio-Installer aktualisiert. Mit dem zweiten Befehl wird die Visual Studio-Instanz aktualisiert. Um zu verhindern, dass ein Dialogfeld zur Benutzerkontensteuerung angezeigt wird, führen Sie die Eingabeaufforderung als Administrator aus.

* Installieren Sie automatisch eine Desktopinstanz von Visual Studio mit dem französischen Sprachpaket, die nur zurückgegeben wird, wenn das Produkt aufgerufen wird.

  ```cmd
  vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

  > [!NOTE]
  > Der `--wait`-Parameter ist für die Verwendung in einer Batchdatei bestimmt. In einer Batchdatei wird die Ausführung des nächsten Befehls nicht fortgesetzt, bis die Installation abgeschlossen ist. Die `%ERRORLEVEL%`-Umgebungsvariable enthält den Rückgabewert des Befehls, so wie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md) dokumentiert.

## <a name="using---layout"></a>Verwenden von „--layout“

* Laden Sie den Visual Studio-Kern-Editor (die minimalste Visual Studio-Konfiguration) herunter. Schließen Sie nur das englische Sprachpaket ein:

  ```cmd
  vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Laden Sie die .NET-Desktop- und .NET-Web-Arbeitsauslastungen zusammen mit allen empfohlenen Komponenten und der GitHub-Erweiterung herunter. Schließen Sie nur das englische Sprachpaket ein:

  ```cmd
  vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---includerecommended"></a>Verwenden von „--includeRecommended“

* Starten Sie eine interaktive Installation aller Arbeitsauslastungen und Komponenten, die in der Visual Studio 2017 Enterprise-Edition verfügbar sind:

  ```cmd
  vs_enterprise.exe --all --includeRecommended --includeOptional
  ```

* Installierten Sie eine zweite, benannte Instanz von Visual Studio 2017 Professional auf einem Computer, auf dem die Visual Studio 2017 Community-Edition bereits mit der Unterstützung für die Node.js-Entwicklung enthalten ist.

  ```cmd
  vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Verwenden von „--remove“

* Entfernen Sie die Komponente des Profilerstellungstools von der Standardinstanz, die auf Visual Studio installiert ist:

  ```cmd
  vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

## <a name="using---path"></a>Verwenden von „--path“

Diese Befehlszeilenparameter sind **neu in Version 15.7**. Weitere Informationen zu Befehlszeilenparametern finden Sie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Verwenden der Pfade „install“, „cache“ und „shared“:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Ausschließliches Verwenden der Pfade „install“ und „cache“:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Ausschließliches Verwenden der Pfade „install“ und „shared“:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Ausschließliches Verwenden des „install“-Pfads:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Verwenden von „export“

Dieser Befehlszeilenbefehl ist **neu in 15.9**. Weitere Informationen finden Sie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Verwenden von „export“ zum Speichern der Auswahl einer Installation:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
```

* Verwenden von „export“ zum Speichern einer neu erstellten benutzerdefinierten Auswahl:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
```

## <a name="using---config"></a>Verwenden von „--config“

Dieser Befehlszeilenparameter ist **neu in 15.9**. Weitere Informationen finden Sie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Verwenden von „--config“ zum Installieren der Workloads und der Komponenten aus einer kürzlich gespeicherten Installationskonfigurationsdatei:

```cmd
vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
```

* Verwenden von „--config“ zum Hinzufügen von Workloads und Komponenten zu einer bereits vorhandenen Installation:

```cmd
vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
```


[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Administratorhandbuch für Visual Studio](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Erstellen einer Offlineinstallation von Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
