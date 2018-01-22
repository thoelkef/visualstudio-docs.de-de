---
title: "Projekteinstellungen für C#-Debugkonfigurationen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 054a015c5fcd6a70696ed6945faa5cbd01547168
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2018
---
# <a name="project-settings-for--c-debug-configurations"></a>Projekteinstellungen für C#-Debugkonfigurationen
Sie können die projekteinstellungen für eine C#-Debugkonfiguration im Ändern der **Eigenschaftenseiten** Fenster entsprechend der Anleitung unter [Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Die folgenden Tabellen zeigen, wo die debuggerspezifischen Einstellungen im Suchen der **Eigenschaftenseiten** Fenster.  
  
> [!WARNING]
>  Dieses Thema gilt nicht für UWP-Apps. Finden Sie unter [Starten einer Debugsitzung (VB, c#, C++ und XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a>Registerkarte "Debuggen"  
  
|**Einstellung**|**Beschreibung**|  
|-----------------|---------------------|  
|**Konfiguration**|Legt den Modus für das Kompilieren der Anwendung fest. Wählen Sie zwischen **aktiv (Debuggen)**, **Debuggen**, **Release**, **alle Konfigurationen**.|  
|**Startaktion**|Anhand dieser Gruppe von Steuerungen wird festgelegt, welche Aktion bei Auswahl von Starten im Menü Debuggen erfolgt.<br /><br /> -   **Starten Sie Projekt** ist die Standardeinstellung und das Startprojekt zum Debuggen gestartet. Weitere Informationen finden Sie unter [auswählen des Startprojekts](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Externes Programm starten** ermöglicht es Ihnen zu starten, Anfügen an ein Programm, das nicht Teil einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt. Weitere Informationen finden Sie unter [Anfügen an ein aktives Programm](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Browser mit folgender URL starten** ermöglicht es Ihnen, eine Webanwendung Debuggen.|  
|**Befehlszeilenargumente**|Legt Befehlszeilenargumente für das Programm fest, das gedebuggt werden soll. Der Befehlsname entspricht dem unter Externes Programm starten angegebenen Programmnamen. Wenn für Startaktion die Option Start-URL ausgewählt ist, können keine Befehlszeilenargumente festgelegt werden.|  
|**Arbeitsverzeichnis**|Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird. Das Arbeitsverzeichnis in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ist das Verzeichnis, aus dem die Anwendung gestartet wird. Standardmäßig ist dies das Verzeichnis \bin\debug.|  
|**Remotecomputer verwenden**|Der Name eines Remotecomputers, auf dem die Anwendung wird ausgeführt, für Debugzwecke oder ein [Msvsmon-Servernamen](../debugger/remote-debugging.md). Der Speicherort der EXE-Datei auf dem Remotecomputer wird durch die Eigenschaft Ausgabepfad festgelegt, die sich im Ordner Konfigurationseigenschaften in der Kategorie Erstellen befindet. Bei diesem Speicherort muss es sich um ein freigegebenes Verzeichnis auf dem Remotecomputer handeln.|
|**Nicht verwaltetes Codedebuggen aktivieren**|Bietet die Möglichkeit, Aufrufe von systemeigenem (nicht verwaltetem) Win32-Code von einer verwalteten Anwendung aus zu debuggen.|  
|**SQL Server-Debuggen aktivieren**|Ermöglicht das Debuggen von SQL Server-Datenbankobjekten.|  
  
##  <a name="BKMK_Build_tab"></a>Registerkarte "erstellen"  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Symbole für bedingte Kompilierung:**|Hier werden die Konstanten DEBUG und TRACE definiert.<br /><br /> Diese Konstanten unterstützen die bedingte Kompilierung von der [Debug-Klasse](/dotnet/api/system.diagnostics.debug) und [Trace-Klasse](/dotnet/api/system.diagnostics.trace). Diese Konstanten definiert, Debug und Trace Klassenmethode Ausgabewerte erzeugt werden, die [Fenster "Ausgabe"](../ide/reference/output-window.md). Ohne diese Konstanten werden die Klassenmethoden Debug und Trace nicht kompiliert und keine Ausgabe erzeugt.<br /><br /> -Debug ist normalerweise in der Debugversion eines Programms definiert und in der Releaseversion nicht definiert.<br />-Traceaktionen werden normalerweise in der Debug-und Releaseversion definiert.|  
|**Code optimieren**|Sofern Sie keinen Fehler finden, der ausschließlich in optimiertem Code auftritt, sollte diese Einstellung in der Debugversion deaktiviert bleiben. Optimierter Code ist aufwendiger zu debuggen, da die Anweisungen nicht direkt mit den Anweisungen in den Quellcodefenstern übereinstimmen.|  
|**Ausgabepfad:**|Wird zum Debuggen normalerweise auf "bin\Debug" festgelegt.|

> [!NOTE]
> Weitere Informationen zu Debugoptionen Sie in finden der **erweitert** Schaltfläche, finden Sie unter [Dialogfeld "Erweiterte Buildeinstellungen" (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Die portable für Symboldateien (.pdb) ist das letzte plattformübergreifende Format für .NET Core. 
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)