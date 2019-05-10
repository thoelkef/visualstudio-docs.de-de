---
title: Projekteinstellungen für eine C# Config Debuggen | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5108e195e5df245c72436752316e8ee91781e7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62904011"
---
# <a name="project-settings-for--c-debug-configurations"></a>Projekteinstellungen für C#-Debugkonfigurationen

Sie können ändern, C# Debug-projekteinstellungen in die [Registerkarte "Debuggen"](#debug-tab) und [Registerkarte "Build"](#build-tab) der Eigenschaftenseiten des Projekts.

Um die Eigenschaftenseiten zu öffnen, wählen Sie das Projekt im **Projektmappen-Explorer** und wählen Sie dann die **Eigenschaften** Symbol, oder mit der rechten Maustaste in des Projekts, und wählen Sie **Eigenschaften**.

Weitere Informationen finden Sie unter [Debug and release configurations (Debug- und Releasekonfigurationen)](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>Diese Einstellungen gelten nicht für .NET Core, ASP.NET oder UWP-apps. Um die Einstellungen zum Debuggen für UWP-apps konfigurieren zu können, finden Sie unter [Starten einer Debugsitzung für UWP-Apps](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

## <a name="debug-tab"></a>Registerkarte "Debuggen"

|Einstellung|Beschreibung|
|-------------------------------------| - |
| **Konfiguration** | Legt den Modus zum Erstellen der app. Wählen Sie **aktiv (Debuggen)**, **Debuggen**, **Version**, oder **alle Konfigurationen** aus der Dropdownliste aus. |
| **Startaktion** | Gibt die Aktion an, bei der Auswahl **starten** in einem Debug-Konfiguration.<br />- Durch den Standardwert **Projekt starten**, wird das Startprojekt zum Debuggen gestartet. Weitere Informationen finden Sie unter [auswählen des Startprojekts](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Externes Programm starten** startet und wird an eine app, die nicht Teil einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt. Weitere Informationen finden Sie unter [Anfügen an laufende Prozesse mit dem Debugger](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Browser mit URL starten** können Sie eine Web-app zu debuggen. |
| **Startoptionen** > **Befehlszeilenargumente** | Gibt Befehlszeilenargumente für die app, die gedebuggt wird. Der Namen des Befehls wird der Name der app im angegebenen **externes Programm starten**. |
| **Startoptionen** > **Arbeitsverzeichnis** | Gibt das Arbeitsverzeichnis für die app, die gedebuggt wird. In C#, das Arbeitsverzeichnis ist *\bin\debug* standardmäßig.
| **Startoptionen** > **Remotecomputer verwenden**|Für das Remotedebuggen, wählen Sie diese Option aus, und geben Sie den Namen der Remotedebugging-Ziel, oder ein [Msvsmon-Servernamen](../debugger/remote-debugging.md). <br />Der Speicherort einer App auf dem Remotecomputer wird angegeben, durch die **Ausgabepfad** Eigenschaft für die **erstellen** Registerkarte. Bei diesem Speicherort muss es sich um ein freigegebenes Verzeichnis auf dem Remotecomputer handeln.
| **Debugger-Engine** > **nicht verwaltetes Codedebuggen aktivieren** | Debuggt Aufrufe von systemeigenem (nicht verwaltetem) Win32-Code aus der verwalteten Anwendung. |
| **Debugger-Engine** > **SQL Server-debugging aktivieren** | Debuggt SQL Server-Datenbankobjekten. |

## <a name="build-tab"></a>Registerkarte "Erstellen"

|Einstellung|Beschreibung|
|-------------|-----------------|
|**Allgemeine** > **Symbole für bedingte Kompilierung**|Wenn ausgewählt, definieren Sie die Konstanten DEBUG und TRACE.<br /><br /> Diese Konstanten ermöglichen das Kompilieren der [Debug-](/dotnet/api/system.diagnostics.debug) und [Trace-Klassen](/dotnet/api/system.diagnostics.trace). Wenn diese Konstanten definiert sind, generieren die Klassenmethoden „Debug“ und „Trace“ eine Ausgabe im [Ausgabefenster](../ide/reference/output-window.md). Ohne diese Konstanten werden die Klassenmethoden Debug und Trace nicht kompiliert und keine Ausgabe erzeugt.<br /><br />DEBUGGEN ist in der Regel in der Debugversion eines Builds definiert und in der Releaseversion nicht definiert. ABLAUFVERFOLGUNG wird in sowohl der Debug-und Releaseversionen definiert.|
|**Allgemeine** > **Code optimieren**|Wenn ein Fehler nur im optimierten Code angezeigt wird, behalten Sie für diese Einstellung für Debugbuilds Auswahl aufgehoben wurde. Optimierter Code ist schwieriger zu debuggen, da Anweisungen nicht direkt mit den Anweisungen im Quellcode übereinstimmen.|
|**Ausgabe** > **Ausgabepfad**|Wird zum Debuggen normalerweise auf *bin\Debug* festgelegt.|
|**Erweiterte** Schaltfläche|Weitere Informationen zu erweiterten Optionen für das Debuggen, finden Sie unter [Erweiterte Buildeinstellungen Einstellungen (Dialogfeld) (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Portable Format für das Symbol (*PDB*) Dateien ist eine aktuelle Cross-Platform-Format für .NET Core-apps.

## <a name="see-also"></a>Siehe auch
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)