---
title: "Projekteinstellungen f&#252;r eine Visual&#160;Basic-Debugkonfiguration | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbProjectPropertiesDebug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugbuilds, Projekteinstellungen"
  - "Debugkonfigurationen, Visual Basic"
  - "Debuggen [Visual Basic], Debuggereinstellungen"
  - "Projektkonfigurationen, Debug"
  - "Projekteinstellungen [Visual Studio], Debugkonfigurationen"
  - "Projekte [Visual Studio], Debugkonfigurationen"
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Projekteinstellungen f&#252;r eine Visual&#160;Basic-Debugkonfiguration
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Projekteinstellungen für eine [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Debugkonfiguration im Fenster **Eigenschaftenseiten** entsprechend der Anleitung unter [Debug\- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md) ändern.  Anhand der folgenden Tabellen erfahren Sie, wo die debuggerspezifischen Einstellungen im Fenster **Eigenschaftenseiten** zu finden sind.  
  
> [!WARNING]
>  Dieses Thema gilt nicht für Store\-Apps.  Siehe [Starten einer Debugsitzung \(VB, C\#, C\+\+ und XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
### Registerkarte "Debuggen"  
  
|Einstellung|Beschreibung|  
|-----------------|------------------|  
|**Konfiguration**|Legt den Modus für das Kompilieren der Anwendung fest.  Sie können **Aktiv \(Debug\)**, **Debuggen**, **Release** oder **Alle Konfigurationen** auswählen.|  
|**Startaktion**|Anhand dieser Gruppe von Steuerungen wird festgelegt, welche Aktion bei Auswahl von **Starten** im Menü **Debuggen** erfolgt.<br /><br /> -   Durch den Standardwert **Startprojekt** wird das Startprojekt zum Debuggen gestartet.  Weitere Informationen finden Sie unter [Gewusst wie: Festlegen von Startprojekten](http://msdn.microsoft.com/de-de/31465836-0911-48db-a5d9-e456b635e970).<br />-   Mithilfe der Option **Externes Programm starten** können Sie ein Programm starten, das nicht zu einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt gehört, und eine Verbindung zu diesem Programm herstellen.  Weitere Informationen finden Sie unter [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   Mithilfe von **Browser mit folgender URL starten** können Sie eine Webanwendung debuggen.|  
|**Befehlszeilenargumente**|Legt Befehlszeilenargumente für das Programm fest, das gedebuggt werden soll.  Der Befehlsname entspricht dem unter **Externes Programm starten** angegebenen Programmnamen.  Wenn die Option Start\-URL für Startaktion ausgewählt ist, werden die Befehlszeilenargumente ignoriert.|  
|**Arbeitsverzeichnis**|Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird.  Das Arbeitsverzeichnis in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ist das Verzeichnis, über das die Anwendung gestartet wird.  Das standardmäßige Arbeitsverzeichnis ist \\bin\\Debug oder \\bin\\Release. Dies hängt von der aktuellen Konfiguration ab.|  
|**Remotecomputer verwenden**|Bei aktiviertem Kontrollkästchen ist das Remotedebuggen aktiviert.  Im Textfeld können Sie den Namen eines Remotecomputers eingeben, auf dem die Anwendung zu Debugzwecken ausgeführt wird, oder einen [Msvsmon\-Servernamen](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  Der Speicherort der EXE\-Datei auf dem Remotecomputer wird in der Registerkarte Erstellen unter der Eigenschaft Ausgabepfad festgelegt.  Bei diesem Speicherort muss es sich um ein freigegebenes Verzeichnis auf dem Remotecomputer handeln.|  
|**Nicht verwalteten Code debuggen**|Bietet die Möglichkeit, Aufrufe von systemeigenem \(nicht verwaltetem\) Win32\-Code von einer verwalteten Anwendung aus zu debuggen.  Wenn Sie in einem [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-Projekt unter Debuggertyp die Option Gemischt auswählen, erzielen Sie denselben Effekt.|  
|**SQL Server\-Debuggen**|Ermöglicht das Debuggen von SQL Server\-Datenbankobjekten.|  
  
### Registerkarte "Kompilieren": Drücken der Schaltfläche "Erweiterte Kompilierungsoptionen"  
  
|Einstellung|Beschreibung|  
|-----------------|------------------|  
|**Optimierungen aktivieren**|Diese Option sollte deaktiviert sein.  Eine Optimierung führt dazu, dass der tatsächlich ausgeführte Code sich von dem in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sichtbaren Quellcode unterscheidet. Dadurch wird das Debuggen erschwert.  Bei einer Codeoptimierung werden Symbole nicht standardmäßig geladen, wenn Sie mit Nur mein Code debuggen.|  
|**Generieren von Debuginformationen**|Standardmäßig in Debugversion und Releaseversion definiert, erstellt diese Einstellung \(gleichwertig mit der Compileroption \/debug\) Debuginformationen zur Buildzeit.  Der Debugger nutzt diese Informationen, um Variablennamen und andere Informationen während des Debuggens in einem sinnvollen Format anzuzeigen.  Wenn Sie das Programm ohne diese Informationen kompilieren, sind die Funktionen des Debuggers eingeschränkt.  Weitere Informationen hierzu finden Sie unter [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|**DEBUG\-Konstante definieren**|Durch die Definition dieses Symbols können Ausgabefunktionen aus der [Debug\-Klasse](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx) bedingt kompiliert werden.  Wenn dieses Symbol definiert ist, generieren die **Debug**\-Klassenmethoden im [Fenster "Ausgabe"](../ide/reference/output-window.md) eine Ausgabe.  Ohne dieses Symbol werden **Debug**\-Klassenmethoden nicht kompiliert und keine Ausgabe generiert.  In der Debugversion sollte das Symbol definiert sein und in der Releaseversion nicht.  Durch die Definition des Symbols in einer Releaseversion wird überflüssiger Code erstellt, der die Programmleistung beeinträchtigt.|  
|**TRACE\-Konstante definieren**|Durch die Definition dieses Symbols können Ausgabefunktionen der [Trace\-Klasse](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx) bedingt kompiliert werden.  Wenn dieses Symbol definiert ist, generieren die **Trace**\-Klassenmethoden im [Fenster "Ausgabe"](../ide/reference/output-window.md) eine Ausgabe.  Ohne dieses Symbol werden **Trace**\-Klassenmethoden nicht kompiliert und keine **Trace**\-Ausgabe generiert.  Dieses Symbol wird standardmäßig sowohl für Debugversion als auch Releaseversion definiert.|  
  
## Siehe auch  
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)