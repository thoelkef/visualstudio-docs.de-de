---
title: Projekteinstellungen für eine Visual Basic-Debugkonfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25fc12f08e9519a68dd68d98b16099729a2d233b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938252"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Projekteinstellungen für eine Visual Basic-Debugkonfiguration
Sie können ändern, dass die projekteinstellungen für eine [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Debug-Konfiguration in der **Eigenschaftenseiten** Fenster wie in beschrieben [Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Die folgenden Tabellen zeigen, wo Sie debuggerspezifischen Einstellungen im finden die **Eigenschaftenseiten** Fenster.  
  
> [!WARNING]
>  Dieses Thema gilt nicht für UWP-Apps. Finden Sie unter [Starten einer Debugsitzung (VB, c#, C++ und XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Registerkarte "Debuggen"  
  
| Einstellung | Beschreibung |
|------------------------------| - |
| **Konfiguration** | Legt den Modus für das Kompilieren der Anwendung fest. Wählen Sie zwischen **aktiv (Debuggen)**, **Debuggen**, **Version**, **alle Konfigurationen**. |
| **Startaktion** | Anhand dieser Gruppe von Steuerungen wird festgelegt, welche Aktion bei Auswahl von Starten im Menü Debuggen erfolgt.<br /><br /> -   **Projekt starten** ist die Standardeinstellung und startet das Startprojekt zum Debuggen. <br />-   **Externes Programm starten** ermöglicht Ihnen das Starten und Anfügen an ein Programm, das nicht Teil einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Browser starten, in der URL** ermöglicht es Ihnen, eine Webanwendung Debuggen. |
| **Befehlszeilenargumente** | Legt Befehlszeilenargumente für das Programm fest, das gedebuggt werden soll. Der Befehlsname entspricht dem unter Externes Programm starten angegebenen Programmnamen. Wenn die Option Start-URL für Startaktion ausgewählt ist, werden die Befehlszeilenargumente ignoriert. |
| **Arbeitsverzeichnis** | Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird. Das Arbeitsverzeichnis in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ist das Verzeichnis, über das die Anwendung gestartet wird. Das standardmäßige Arbeitsverzeichnis ist \bin\Debug oder \bin\Release, abhängig von der aktuellen Konfiguration an. |
| **Remoten Computer verwenden** | Bei aktiviertem Kontrollkästchen ist das Remotedebuggen aktiviert. Im Textfeld können Sie die Namen von einem Remotecomputer, in dem die Anwendung wird ausgeführt, für Debugzwecke eingeben oder ein [Msvsmon-Servernamen](../debugger/remote-debugging.md). Der Speicherort der EXE-Datei auf dem Remotecomputer wird in der Registerkarte Erstellen unter der Eigenschaft Ausgabepfad festgelegt. Bei diesem Speicherort muss es sich um ein freigegebenes Verzeichnis auf dem Remotecomputer handeln. |
| **Debuggen von nicht verwaltetem code** | Bietet die Möglichkeit, Aufrufe von systemeigenem (nicht verwaltetem) Win32-Code von einer verwalteten Anwendung aus zu debuggen. Wenn Sie in einem [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projekt unter Debuggertyp die Option Gemischt auswählen, erzielen Sie denselben Effekt. |
| **SQL Server-debugging** | Ermöglicht das Debuggen von SQL Server-Datenbankobjekten. |
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Registerkarte "Kompilieren": Drücken der Schaltfläche "Erweiterte Kompilierungsoptionen"  
  
| Einstellung | Beschreibung |
|---------------------------| - |
| **Optimierungen aktivieren** | Diese Option sollte deaktiviert sein. Eine Optimierung führt dazu, dass der tatsächlich ausgeführte Code sich von dem in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sichtbaren Quellcode unterscheidet. Dadurch wird das Debuggen erschwert. Bei einer Codeoptimierung werden Symbole nicht standardmäßig geladen, wenn Sie mit Nur mein Code debuggen. |
| **Generieren von Debuginformationen** | Standardmäßig in Debugversion und Releaseversion definiert, erstellt diese Einstellung (gleichwertig mit der Compileroption /debug) Debuginformationen zur Buildzeit. Der Debugger nutzt diese Informationen, um Variablennamen und andere Informationen während des Debuggens in einem sinnvollen Format anzuzeigen. Wenn Sie das Programm ohne diese Informationen kompilieren, sind die Funktionen des Debuggers eingeschränkt. Weitere Informationen finden Sie unter [/debug](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| **DEBUG-Konstante definieren** | Durch die Definition dieses Symbols kann Ausgabefunktionen aus bedingt kompiliert die [Debug-Klasse](/dotnet/api/system.diagnostics.debug). Dieses Symbol definiert ist, Debug-Klasse, Methoden generieren die [Fenster "Ausgabe"](../ide/reference/output-window.md). Ohne dieses Symbol werden Debug-Klassenmethoden nicht kompiliert und keine Ausgabe generiert. In der Debugversion sollte das Symbol definiert sein und in der Releaseversion nicht. Durch die Definition des Symbols in einer Releaseversion wird überflüssiger Code erstellt, der die Programmleistung beeinträchtigt. |
| **TRACE-Konstante definieren** | Durch die Definition dieses Symbols kann Ausgabefunktionen aus bedingt kompiliert die [Trace-Klasse](/dotnet/api/system.diagnostics.trace). Dieses Symbol definiert ist, die Methoden der Trace-Klasse generieren die [Fenster "Ausgabe"](../ide/reference/output-window.md). Ohne dieses Symbol werden Trace-Klassenmethoden nicht kompiliert und keine Trace-Ausgabe generiert. Dieses Symbol wird standardmäßig sowohl für Debugversion als auch Releaseversion definiert. |
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)