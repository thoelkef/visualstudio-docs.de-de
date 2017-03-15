---
title: "Projekteinstellungen f&#252;r C#-Debugkonfigurationen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugbuilds, Projekteinstellungen"
  - "Debugkonfigurationen, C#"
  - "Debugkonfigurationen, J#"
  - "Debuggen [C#], Debuggereinstellungen"
  - "Debuggen [J#], Debuggereinstellungen"
  - "Projektkonfigurationen, Debug"
  - "Projekteinstellungen [Visual Studio], Debugkonfigurationen"
  - "Projekte [Visual Studio], Debugkonfigurationen"
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Projekteinstellungen f&#252;r C#-Debugkonfigurationen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Projekteinstellungen für eine C\#\-Debugkonfiguration im Fenster **Eigenschaftenseiten** entsprechend der Anleitung unter [Debug\- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md) ändern.  Anhand der folgenden Tabellen erfahren Sie, wo die debuggerspezifischen Einstellungen im Fenster **Eigenschaftenseiten** zu finden sind.  
  
> [!WARNING]
>  Dieses Thema gilt nicht für Windows Store\-Apps.  Siehe [Starten einer Debugsitzung \(VB, C\#, C\+\+ und XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Registerkarte "Debuggen"  
  
|**Einstellung**|**Beschreibung**|  
|---------------------|----------------------|  
|**Konfiguration**|Legt den Modus für das Kompilieren der Anwendung fest.  Sie können **Aktiv \(Debug\)**, **Debuggen**, **Release** oder **Alle Konfigurationen** auswählen.|  
|**Startvorgang**|Anhand dieser Gruppe von Steuerungen wird festgelegt, welche Aktion bei Auswahl von Starten im Menü Debuggen erfolgt.<br /><br /> -   Durch den Standardwert **Startprojekt** wird das Startprojekt zum Debuggen gestartet.  Weitere Informationen finden Sie unter [Auswählen des Startprojekts](http://msdn.microsoft.com/de-de/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   Mithilfe der Option **Externes Programm starten** können Sie ein Programm starten, das nicht zu einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt gehört, und eine Verbindung zu diesem Programm herstellen.  Weitere Informationen finden Sie unter [Anfügen an ein aktives Programm](http://msdn.microsoft.com/de-de/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   Mithilfe von **Browser mit folgender URL starten** können Sie eine Webanwendung debuggen.|  
|**Befehlszeilenargumente**|Legt Befehlszeilenargumente für das Programm fest, das gedebuggt werden soll.  Der Befehlsname entspricht dem unter Externes Programm starten angegebenen Programmnamen.  Wenn für Startaktion die Option Start\-URL ausgewählt ist, können keine Befehlszeilenargumente festgelegt werden.|  
|**Arbeitsverzeichnis**|Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird.  Das Arbeitsverzeichnis in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ist das Verzeichnis, aus dem die Anwendung gestartet wird. Standardmäßig ist dies das Verzeichnis \\bin\\debug.|  
|**Remoten Computer verwenden**|Der Name eines Remotecomputers, auf dem die Anwendung zu Debugzwecken ausgeführt wird, oder ein [Msvsmon\-Servername](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  Der Speicherort der EXE\-Datei auf dem Remotecomputer wird durch die Eigenschaft Ausgabepfad festgelegt, die sich im Ordner Konfigurationseigenschaften in der Kategorie Erstellen befindet.  Bei diesem Speicherort muss es sich um ein freigegebenes Verzeichnis auf dem Remotecomputer handeln.|  
|**Nicht verwaltetes Codedebuggen aktivieren**|Bietet die Möglichkeit, Aufrufe von systemeigenem \(nicht verwaltetem\) Win32\-Code von einer verwalteten Anwendung aus zu debuggen.|  
|**SQL Server\-Debuggen aktivieren**|Ermöglicht das Debuggen von SQL Server\-Datenbankobjekten.|  
  
##  <a name="BKMK_Build_tab"></a> Registerkarte "Erstellen"  
  
|Einstellung|Beschreibung|  
|-----------------|------------------|  
|**Symbole für bedingte Kompilierung:**|Hier werden die Konstanten DEBUG und TRACE definiert.<br /><br /> Diese Konstanten unterstützen die bedingte Kompilierung der [Debug\-Klasse](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx) und der [Trace\-Klasse](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx).  Wenn diese Konstanten definiert sind, generieren die [Debug](../ide/reference/output-window.md)\-Klassenmethode und die Trace Klassenmethode im Fenster "Ausgabe" eine Ausgabe.  Ohne diese Konstanten werden die Klassenmethoden Debug und Trace nicht kompiliert und keine Ausgabe erzeugt.<br /><br /> -   Debugaktionen werden normalerweise in der Debugversion eines Programms definiert; ihre Definition wird in der Releaseversion wieder aufgehoben.<br />-   Traceaktionen werden normalerweise sowohl in Debugversionen als auch in Releaseversionen definiert.|  
|**Code optimieren**|Sofern Sie keinen Fehler finden, der ausschließlich in optimiertem Code auftritt, sollte diese Einstellung in der Debugversion deaktiviert bleiben.  Optimierter Code ist aufwendiger zu debuggen, da die Anweisungen nicht direkt mit den Anweisungen in den Quellcodefenstern übereinstimmen.|  
|**Ausgabepfad:**|Wird zum Debuggen normalerweise auf "bin\\Debug" festgelegt.|  
  
## Siehe auch  
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)