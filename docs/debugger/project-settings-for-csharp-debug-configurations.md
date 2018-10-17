---
title: Projekteinstellungen für C#-Debugkonfigurationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c5bd49d550cb03e8234c8740ea8c0f605ed721c2
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283261"
---
# <a name="project-settings-for--c-debug-configurations"></a>Projekteinstellungen für C#-Debugkonfigurationen
Sie können die projekteinstellungen für eine C#-Debugkonfiguration im Ändern der **Eigenschaftenseiten** Fenster wie in beschrieben [Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Die folgenden Tabellen zeigen, wo Sie debuggerspezifischen Einstellungen im finden die **Eigenschaftenseiten** Fenster.  
  
> [!WARNING]
>  Dieses Thema gilt nicht für UWP-Apps. Finden Sie unter [Starten einer Debugsitzung (VB, c#, C++ und XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Registerkarte "Debuggen"  
  
|**Einstellung**|**Beschreibung**|  
|-----------------|---------------------|  
|**Konfiguration**|Legt den Modus für das Kompilieren der Anwendung fest. Wählen Sie zwischen **aktiv (Debuggen)**, **Debuggen**, **Version**, **alle Konfigurationen**.|  
|**Startaktion**|Anhand dieser Gruppe von Steuerungen wird festgelegt, welche Aktion bei Auswahl von Starten im Menü Debuggen erfolgt.<br /><br /> -   **Projekt starten** ist die Standardeinstellung und startet das Startprojekt zum Debuggen. Weitere Informationen finden Sie unter [auswählen des Startprojekts](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />-   **Externes Programm starten** ermöglicht Ihnen das Starten und Anfügen an ein Programm, das nicht Teil einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt. Weitere Informationen finden Sie unter [Anfügen an ein aktives Programm](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z(v=vs.100)).<br />-   **Browser starten, in der URL** ermöglicht es Ihnen, eine Webanwendung Debuggen.|  
|**Befehlszeilenargumente**|Legt Befehlszeilenargumente für das Programm fest, das gedebuggt werden soll. Der Befehlsname entspricht dem unter Externes Programm starten angegebenen Programmnamen. Wenn für Startaktion die Option Start-URL ausgewählt ist, können keine Befehlszeilenargumente festgelegt werden.|  
|**Arbeitsverzeichnis**|Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird. Das Arbeitsverzeichnis in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ist das Verzeichnis, aus dem die Anwendung gestartet wird. Standardmäßig ist dies das Verzeichnis \bin\debug.|  
|**Remotecomputer verwenden**|Der Name eines Remotecomputers, in dem die Anwendung wird ausgeführt, für Debugzwecke oder [Msvsmon-Servernamen](../debugger/remote-debugging.md). Der Speicherort der EXE-Datei auf dem Remotecomputer wird durch die Eigenschaft Ausgabepfad festgelegt, die sich im Ordner Konfigurationseigenschaften in der Kategorie Erstellen befindet. Bei diesem Speicherort muss es sich um ein freigegebenes Verzeichnis auf dem Remotecomputer handeln.|
|**Nicht verwaltetes Codedebuggen aktivieren**|Bietet die Möglichkeit, Aufrufe von systemeigenem (nicht verwaltetem) Win32-Code von einer verwalteten Anwendung aus zu debuggen.|  
|**SQL Server-Debuggen aktivieren**|Ermöglicht das Debuggen von SQL Server-Datenbankobjekten.|  
  
##  <a name="BKMK_Build_tab"></a> Registerkarte "erstellen"  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Symbole für bedingte Kompilierung:**|Hier werden die Konstanten DEBUG und TRACE definiert.<br /><br /> Diese Konstanten unterstützen die bedingte Kompilierung von der [Debug-Klasse](/dotnet/api/system.diagnostics.debug) und [Trace-Klasse](/dotnet/api/system.diagnostics.trace). Diese Konstanten definiert, Debuggen und Trace-Klasse, Methoden Generieren von Ausgaben für die [Fenster "Ausgabe"](../ide/reference/output-window.md). Ohne diese Konstanten werden die Klassenmethoden Debug und Trace nicht kompiliert und keine Ausgabe erzeugt.<br /><br /> -Debug ist normalerweise in der Debugversion eines Programms definiert und in der Releaseversion nicht definiert.<br />-Ablaufverfolgung wird normalerweise in sowohl Debug-und Releaseversionen definiert.|  
|**Code optimieren**|Sofern Sie keinen Fehler finden, der ausschließlich in optimiertem Code auftritt, sollte diese Einstellung in der Debugversion deaktiviert bleiben. Optimierter Code ist aufwendiger zu debuggen, da die Anweisungen nicht direkt mit den Anweisungen in den Quellcodefenstern übereinstimmen.|  
|**Ausgabepfad:**|Wird zum Debuggen normalerweise auf "bin\Debug" festgelegt.|

> [!NOTE]
> Weitere Informationen zu Debugoptionen Sie in finden der **erweitert** Schaltfläche, finden Sie unter [Dialogfeld "Erweiterte Buildeinstellungen" (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Die portable für Symboldateien (.pdb) ist das neueste Cross-Platform-Format für .NET Core. 
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)