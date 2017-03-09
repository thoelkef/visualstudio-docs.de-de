---
title: "Debuggen einer Anwendung mit Dumpdateien, falls sie in Visual Studio abst&#252;rzt oder nicht mehr reagiert | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.crashdump"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Crashdumps"
  - "Dumpdateien"
  - "Dumps"
  - "Dumps, Informationen über Dumps"
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 53
caps.handback.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen einer Anwendung mit Dumpdateien, falls sie in Visual Studio abst&#252;rzt oder nicht mehr reagiert
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dumpdateien mit oder ohne Heaps, Erstellen einer Dumpdatei, Öffnen einer Dumpdatei, Suchen einer Binär\-, PDB\- und Quelldatei für eine Dumpdatei  
  
##  <a name="BKMK_Contents"></a> Inhalt  
 [Was ist eine Dumpdatei?](#BKMK_What_is_a_dump_file_)  
  
 [Dumpdateien, mit oder ohne Heaps](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Anforderungen und Einschränkungen](#BKMK_Requirements_and_limitations)  
  
 [Erstellen einer Dumpdatei](#BKMK_Create_a_dump_file)  
  
 [Öffnen einer Dumpdatei](#BKMK_Open_a_dump_file)  
  
 [Suchen von Binär-, Symbol- (PDB-) und Quelldateien](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
##  <a name="BKMK_What_is_a_dump_file_"></a> Was ist eine Dumpdatei?  
 Eine *Dumpdatei* stellt eine Momentaufnahme einer Anwendung zum Zeitpunkt der Dumperstellung dar.  Sie zeigt, welche Prozesse ausgeführt und welche Module geladen wurden.  Wenn der Dump mit Heapinformationen gespeichert wurde, enthält die Dumpdatei eine Momentaufnahme des Inhalts im Speicher der Anwendung zu diesem Zeitpunkt.  Das Öffnen einer Dumpdatei mit einem Heap in Visual Studio ist vergleichbar mit dem Anhalten an einem Haltepunkt in einer Debugsitzung.  Obwohl die Ausführung nicht fortgesetzt werden kann, können Sie die Stapel\-, Threads\- und Variablenwerte der Anwendung zum Zeitpunkt des Auftretens des Dumps überprüfen.  
  
 Dumpdateien werden hauptsächlich für das Debuggen von Problemen auf Computern verwendet, auf die der Entwickler nicht zugreifen kann.  Sie können beispielsweise eine Dumpdatei vom Computer eines Kunden verwenden, wenn der Absturz des Kundencomputers nicht reproduzierbar oder Ihr Computer blockiert ist.  Dumpdateien werden auch von Testern erstellt, um Absturz\- oder Blockierungsdaten zu sichern, sodass der Testcomputer für weitere Tests verwendet werden kann.  Der Visual Studio\-Debugger kann Dumpdateien für verwalteten oder systemeigenen Code speichern.  Der Debugger kann Dumpdateien laden, die von Visual Studio oder von anderen Programmen erstellt wurden, die Dateien im *Minidumpformat* speichern.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Dumpdateien, mit oder ohne Heaps  
 Sie können Dumpdateien mit oder ohne Heapinformationen erstellen.  
  
-   **Dumpdateien mit Heaps** enthalten eine Momentaufnahme des Speichers der Anwendung.  Dies umfasst die Werte der Variablen zum Zeitpunkt der Dumperstellung.  Wenn Sie eine mit Heaps gespeicherte Dumpdatei laden, können die Symbole in Visual Studio geladen werden, auch wenn die Binärdateien der Anwendung nicht gefunden werden.  Visual Studio speichert auch die Binärdateien der geladenen systemeigenen Module in der Dumpdatei, wodurch das Debugging wesentlich vereinfacht wird.  
  
-   **Dumpdateien ohne Heaps** sind wesentlich kleiner als Dumpdateien mit Heapinformationen.  Allerdings muss der Debugger die Binärdateien der Anwendung laden, um die Symbolinformationen zu finden.  Die Binärdateien müssen exakt mit den Binärdateien übereinstimmen, die für die Erstellung der Dumpdatei verwendet wurden.  In den Dumpdateien ohne Heapdaten werden nur die Werte von Stapelvariablen gespeichert.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Requirements_and_limitations"></a> Anforderungen und Einschränkungen  
  
-   Das Debuggen von Dumpdateien mit optimiertem Code kann unübersichtlich sein.  Beispielsweise kann das Compiler\-Inlining von Funktionen unerwartete Aufruflisten ergeben, und andere Optimierungen könnten die Lebensdauer der Variablen beeinflussen.  
  
-   Dumpdateien von 64\-Bit\-Computern müssen auf einer Instanz von Visual Studio debuggt werden, das auf einem 64\-Bit\-Computer ausgeführt wird.  
  
-   In Visual Studio\-Versionen vor Visual Studio 2013 konnten Dumps von 32\-Bit\-Apps, die auf 64\-Bit\-Computern ausgeführt und mit einigen Tools erfasst wurden \(z. B. Task\-Manager und 64\-Bit WinDbg\), nicht in Visual Studio geöffnet werden.  Diese Einschränkung wurde in Visual Studio 2013 aufgehoben.  
  
-   Visual Studio kann Dumpdateien systemeigener Anwendungen von ARM\-Geräten debuggen.  Visual Studio kann auch Dumpdateien verwalteter Anwendungen von ARM\-Geräten debuggen, jedoch nur im systemeigenen Debugger.  
  
-   Zum Debuggen von [Kernelmodus\-](http://msdn.microsoft.com/library/windows/hardware/ff551880.aspx)\-Dumpdateien in Visual Studio 2013 laden Sie sich die [Windows 8.1\-Version der Debugtools für Windows](http://msdn.microsoft.com/windows/hardware/gg463009) herunter.  Siehe [Kernel\-Debugging in Visual Studio](http://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
-   Visual Studio kann keine Dumpdateien speichern, die im älteren Dumpformat gespeichert wurden. Dieses ältere Dumpformat wird auch als [Vollständiger Benutzermodusdump](http://msdn.microsoft.com/library/windows/hardware/ff545506.aspx) bezeichnet.  Beachten Sie, dass ein vollständiger Benutzermodusdump nicht mit einer Dumpdatei mit Heapinformationen identisch ist.  
  
-   Um mit [SOS.dll \(SOS Debugging Extension\)](../Topic/SOS.dll%20\(SOS%20Debugging%20Extension\).md) in Visual Studio zu debuggen, müssen Sie die Debugtools für Windows installieren, die Bestandteil des Windows\-Treiberkits \(WDK\) sind.  Siehe [Vorschau auf Windows 8.1: Download\-Kits, \-Bits und \-Tools](http://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Create_a_dump_file"></a> Erstellen einer Dumpdatei  
 So erstellen Sie eine Dumpdatei mit Visual Studio  
  
-   Beim Debuggen eines Prozesses in Visual Studio können Sie eine Dumpdatei speichern, wenn der Debugger an einer Ausnahme oder an einem Haltepunkt angehalten wurde.  Wählen Sie **Debuggen**, **Dump speichern unter**.  Wählen Sie im Dialogfeld **Dump speichern unter** in der Liste **Dateityp** die Option **Minidump** oder **Minidump mit Heap** \(Standardeinstellung\) aus.  
  
-   Wenn Sie [Just\-In\-Time\-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md) aktiviert haben, können Sie den Debugger an einen abgestürzten Prozess anfügen, der außerhalb des Debuggers ausgeführt wird, und dann in einer Dumpdatei speichern.  Siehe [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
 Dumpdateien können auch mit jedem Programm erstellt werden, das das Windows\-Minidumpformat unterstützt.  Das **Procdump**\-Eingabeaufforderungs\-Hilfsprogramm von [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) kann beispielsweise  anhand von Triggern oder bedarfsabhängig Dumpdateien zu Prozessabstürzen generieren.  Weitere Informationen zur Verwendung anderer Tools zum Erstellen von Dumpdateien finden Sie unter [Anforderungen und Einschränkungen](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) in diesem Thema.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Open_a_dump_file"></a> Öffnen einer Dumpdatei  
  
1.  Klicken Sie in Visual Studio auf **Datei**, **Öffnen**, **Datei**.  
  
2.  Wählen Sie im Dialogfeld **Datei öffnen** die Dumpdatei aus.  Die Dateinamenerweiterung lautet in der Regel .dmp.  Wählen Sie dann **OK**.  
  
3.  Das Fenster **Zusammenfassung der Minidump\-Datei** wird angezeigt.  In diesem Fenster können Sie Debug\-Zusammenfassungsinformationen für die Dumpdatei anzeigen, den Symbolpfad festlegen, den Debugvorgang starten und die Zusammenfassungsinformationen in die Zwischenablage kopieren.  
  
     ![Minidump&#45;Zusammenfassungsseite](../debugger/media/dbg_dump_summarypage.png "DBG\_DUMP\_SummaryPage")  
  
4.  Klicken Sie im Abschnitt **Aktionen** auf die Option für **Debuggen von ausschließlich systemeigenem Code** oder **Debuggen von gemischtem Code**, um den Debugvorgang zu starten.  
  
##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Suchen von Binär\-, Symbol\- \(PDB\-\) und Quelldateien  
 Um die vollständigen Funktionen von Visual Studio zum Debuggen von Dumpdateien zu nutzen, benötigen Sie Zugriff auf die folgenden Dateien:  
  
-   Die EXE\-Datei, für die der Dump erstellt wurde, sowie andere Binärdateien \(DLLs, usw.\), die im Dumpprozess verwendet wurden.  
  
     Wenn Sie eine Dumpdatei mit Heapdaten debuggen, kann Visual Studio mit fehlenden Binärdateien für einige Module umgehen, es müssen jedoch Binärdateien für genügend Module vorhanden sein, um gültige Aufruflisten generieren zu können.  Visual Studio schließt die systemeigenen Module in einer Dumpdatei mit Heapinformationen ein.  
  
-   Symboldateien \(PDB\-Dateien\) für die EXE\-Datei und andere Binärdateien.  
  
-   Quelldateien für die Module, die Sie interessieren.  
  
     Die ausführbaren Dateien und die PDB\-Dateien müssen exakt mit der Version und dem Build der Dateien übereinstimmen, die für die Erstellung der Dumpdatei verwendet wurden.  
  
     Sie können mithilfe der Disassemblys der Module debuggen, wenn Sie die Quelldateien nicht finden können.  
  
 **Standardsuchpfade für ausführbare Dateien**  
  
 Visual Studio sucht automatisch diese Speicherorte für ausführbare Dateien, die nicht in der Dumpdatei enthalten sind:  
  
1.  Das Verzeichnis mit der Dumpdatei.  
  
2.  Der Pfad des Moduls, der in der Dumpdatei angegeben ist.  Dies ist der Modulpfad auf dem Computer, auf dem das Speicherabbild erfasst wurde.  
  
3.  Die Symbolpfade sind auf der Seite **Debugging**, **Optionen**, **Symbole** im Visual Studio\-Dialogfeld **Tools**, **Optionen** angegeben.  Sie können mehr Speicherorte für die Suche auf dieser Seite hinzufügen.  
  
 **Verwenden der Seite "Keine Binärdatei gefunden", "Keine Symbole gefunden", "Quelle nicht gefunden"**  
  
 Wenn Visual Studio die Dateien nicht finden kann, die zum Debuggen eines Moduls im Dump erforderlich sind, wird eine entsprechende Seite angezeigt \(**Keine Binärdatei gefunden**, **Keine Symbole gefunden** oder **Quelle nicht gefunden**\).  Diese Seiten enthalten ausführliche Informationen zu den Ursachen des Problems und stellen Aktionslinks bereit, mit denen Sie den richtigen Speicherort der Dateien identifizieren können.  Siehe [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
## Siehe auch  
 [Just\-In\-Time\-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Verwenden von IntelliTrace](../debugger/intellitrace.md)