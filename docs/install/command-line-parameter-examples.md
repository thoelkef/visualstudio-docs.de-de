---
title: "Beispiele für die Befehlszeilenparameter für die Installation von Visual Studio | Microsoft-Dokumentation 2017"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: timsneath
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4729300eea0a4e1474779edd4bec021a5db9e73c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Beispiele für die Befehlszeilenparameter für die Installation von Visual Studio 2017
Zur Veranschaulichung, wie [Befehlszeilenparameter zur Installation von Visual Studio](use-command-line-parameters-to-install-visual-studio.md) verwendet werden, sind hier einige Beispiele aufgeführt, die sie Ihren Bedürfnissen anpassen können.

In jedem Beispiel stellen `vs_enterprise.exe`, `vs_professional.exe` und `vs_community.exe` die jeweilige Edition des Visual Studio-Bootstrappers dar, was die kleine Datei ist (ca. 1 MB), die den Downloadprozess initiiert. Wenn Sie eine andere Edition verwenden, ersetzen Sie die entsprechenden Bootstrappernamen.

> [!NOTE]
> Alle Befehle erfordern administrative Erhöhung, und ein Befehl der Benutzerkontensteuerung wird angezeigt, wenn der Prozess nicht von einer erhöhten Aufforderung gestartet wurde.

> [!NOTE]
>  Sie können die `^`-Zeichen am Ende einer Befehlszeile zum Verketten mehrerer Zeilen in einem einzigen Befehl verwenden. Alternativ können Sie einfach diese Zeilen zusammen in einer einzelnen Zeile platzieren. Die Entsprechung in PowerShell ist das Graviszeichen (`` ` ``).

* Installieren Sie eine minimale Instanz von Visual Studio ohne interaktive Anweisungen, aber mit angezeigtem Status:
```
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* Installieren Sie automatisch eine Desktopinstanz von Visual Studio mit dem französischen Sprachpaket, die nur zurückgegeben wird, wenn das Produkt aufgerufen wird.
```
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
```

> [!NOTE]
>  Der `--wait`-Parameter ist für die Verwendung in einer Batchdatei bestimmt. In einer Batchdatei wird die Ausführung des nächsten Befehls nicht fortgesetzt, bis die Installation abgeschlossen ist. Die `%ERRORLEVEL%`-Umgebungsvariable enthält den Rückgabewert des Befehls, so wie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md) dokumentiert.

* Laden Sie den Visual Studio-Kern-Editor (die minimalste Visual Studio-Konfiguration) herunter. Schließen Sie nur das englische Sprachpaket ein:

```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
```

* Laden Sie die .NET-Desktop- und .NET-Web-Arbeitsauslastungen zusammen mit allen empfohlenen Komponenten und der GitHub-Erweiterung herunter. Schließen Sie nur das englische Sprachpaket ein:
```
vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
```

* Starten Sie eine interaktive Installation aller Arbeitsauslastungen und Komponenten, die in der Visual Studio 2017 Enterprise-Edition verfügbar sind:
```
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Installierten Sie eine zweite, benannte Instanz von Visual Studio 2017 Professional auf einem Computer, auf dem die Visual Studio 2017 Community-Edition bereits mit der Unterstützung für die Node.js-Entwicklung enthalten ist.
```
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
```

* Entfernen Sie die Komponente des Profilerstellungstools von der Standardinstanz, die auf Visual Studio installiert ist:
```
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:
* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden.
* Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie auch Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen.  (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

 * [Administratorhandbuch für Visual Studio](visual-studio-administrator-guide.md)
 * [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Erstellen einer Offlineinstallation von Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
