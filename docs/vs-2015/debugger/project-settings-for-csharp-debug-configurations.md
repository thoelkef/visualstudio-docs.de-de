---
title: Projekteinstellungen für C#-Debugkonfigurationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- debugging [J#], debugger settings
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
- debug configurations, J#
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07da36adc1615217315d5ebb23f8ef62db59f5c7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721179"
---
# <a name="project-settings-for--c-debug-configurations"></a>Projekteinstellungen für C#-Debugkonfigurationen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die projekteinstellungen für eine C#-Debugkonfiguration im Ändern der **Eigenschaftenseiten** Fenster wie in beschrieben [Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Die folgenden Tabellen zeigen, wo Sie debuggerspezifischen Einstellungen im finden die **Eigenschaftenseiten** Fenster.  
  
> [!WARNING]
>  Dieses Thema gilt nicht für Windows Store-Apps. Finden Sie unter [Starten einer Debugsitzung (VB, c#, C++ und XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Registerkarte "Debuggen"  
  
|**Einstellung**|**Beschreibung**|  
|-----------------|---------------------|  
|**Konfiguration**|Legt den Modus für das Kompilieren der Anwendung fest. Wählen Sie zwischen **aktiv (Debuggen)**, **Debuggen**, **Version**, **alle Konfigurationen**.|  
|**Startaktion**|Anhand dieser Gruppe von Steuerungen wird festgelegt, welche Aktion bei Auswahl von Starten im Menü Debuggen erfolgt.<br /><br /> -   **Projekt starten** ist die Standardeinstellung und startet das Startprojekt zum Debuggen. Weitere Informationen finden Sie unter [auswählen des Startprojekts](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Externes Programm starten** ermöglicht Ihnen das Starten und Anfügen an ein Programm, das nicht Teil einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projekt. Weitere Informationen finden Sie unter [Anfügen an ein aktives Programm](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Browser starten, in der URL** ermöglicht es Ihnen, eine Webanwendung Debuggen.|  
|**Befehlszeilenargumente**|Legt Befehlszeilenargumente für das Programm fest, das gedebuggt werden soll. Der Befehlsname entspricht dem unter Externes Programm starten angegebenen Programmnamen. Wenn für Startaktion die Option Start-URL ausgewählt ist, können keine Befehlszeilenargumente festgelegt werden.|  
|**Arbeitsverzeichnis**|Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird. Das Arbeitsverzeichnis in [!INCLUDE[csprcs](../includes/csprcs-md.md)] ist das Verzeichnis, aus dem die Anwendung gestartet wird. Standardmäßig ist dies das Verzeichnis \bin\debug.|  
|**Remotecomputer verwenden**|Der Name eines Remotecomputers, in dem die Anwendung wird ausgeführt, für Debugzwecke oder [Msvsmon-Servernamen](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Der Speicherort der EXE-Datei auf dem Remotecomputer wird durch die Eigenschaft Ausgabepfad festgelegt, die sich im Ordner Konfigurationseigenschaften in der Kategorie Erstellen befindet. Bei diesem Speicherort muss es sich um ein freigegebenes Verzeichnis auf dem Remotecomputer handeln.|  
|**Nicht verwaltetes Codedebuggen aktivieren**|Bietet die Möglichkeit, Aufrufe von systemeigenem (nicht verwaltetem) Win32-Code von einer verwalteten Anwendung aus zu debuggen.|  
|**SQL Server-Debuggen aktivieren**|Ermöglicht das Debuggen von SQL Server-Datenbankobjekten.|  
  
##  <a name="BKMK_Build_tab"></a> Registerkarte "erstellen"  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Symbole für bedingte Kompilierung:**|Hier werden die Konstanten DEBUG und TRACE definiert.<br /><br /> Diese Konstanten unterstützen die bedingte Kompilierung von der [Debug-Klasse](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) und [Trace-Klasse](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Diese Konstanten definiert, Debuggen und Trace-Klasse, Methoden Generieren von Ausgaben für die [Fenster "Ausgabe"](../ide/reference/output-window.md). Ohne diese Konstanten werden die Klassenmethoden Debug und Trace nicht kompiliert und keine Ausgabe erzeugt.<br /><br /> -Debug ist normalerweise in der Debugversion eines Programms definiert und in der Releaseversion nicht definiert.<br />-Ablaufverfolgung wird normalerweise in sowohl Debug-und Releaseversionen definiert.|  
|**Code optimieren**|Sofern Sie keinen Fehler finden, der ausschließlich in optimiertem Code auftritt, sollte diese Einstellung in der Debugversion deaktiviert bleiben. Optimierter Code ist aufwendiger zu debuggen, da die Anweisungen nicht direkt mit den Anweisungen in den Quellcodefenstern übereinstimmen.|  
|**Ausgabepfad:**|Wird zum Debuggen normalerweise auf "bin\Debug" festgelegt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)



