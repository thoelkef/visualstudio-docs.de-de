---
title: Verwenden von Dumpdateien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 56
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a2d6215887512f2e0c1410688b2bc924dc1fe3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387056"
---
# <a name="using-dump-files"></a>Verwenden von Abbilddateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dumpdateien mit oder ohne Heaps, Erstellen einer Dumpdatei, Öffnen einer Dumpdatei, Suchen einer Binär-, PDB- und Quelldatei für eine Dumpdatei 
  
## <a name="contents"></a><a name="BKMK_Contents"></a> Inhalt  
 [Was ist eine Dumpdatei?](#BKMK_What_is_a_dump_file_)  
  
 [Dumpdateien, mit oder ohne Heaps](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Anforderungen und Einschränkungen](#BKMK_Requirements_and_limitations)  
  
 [Erstellen einer Dumpdatei](#BKMK_Create_a_dump_file)  
  
 [Öffnen einer Dumpdatei](#BKMK_Open_a_dump_file)  
  
 [Suchen von Binär-, Symbol- (PDB-) und Quelldateien](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
## <a name="what-is-a-dump-file"></a><a name="BKMK_What_is_a_dump_file_"></a> Was ist eine Dumpdatei?  
 Eine *Dumpdatei* ist eine Momentaufnahme einer APP zu dem Zeitpunkt, an dem die Sicherung durchgeführt wird. Sie zeigt, welche Prozesse ausgeführt und welche Module geladen wurden. Wenn der Dump mit Heapinformationen gespeichert wurde, enthält die Dumpdatei eine Momentaufnahme des Inhalts im Speicher der Anwendung zu diesem Zeitpunkt. Das Öffnen einer Dumpdatei mit einem Heap in Visual Studio ist vergleichbar mit dem Anhalten an einem Haltepunkt in einer Debugsitzung. Obwohl die Ausführung nicht fortgesetzt werden kann, können Sie die Stapel-, Threads- und Variablenwerte der Anwendung zum Zeitpunkt des Auftretens des Dumps überprüfen.  
  
 Dumpdateien werden hauptsächlich für das Debuggen von Problemen auf Computern verwendet, auf die der Entwickler nicht zugreifen kann. Beispielsweise können Sie eine Dumpdatei auf dem Computer eines Kunden verwenden, wenn Sie den Absturz oder das nicht reagierende Programm des Kunden auf Ihrem Computer nicht reproduzieren können. Außerdem werden Dumps von Testern erstellt, um Abstürze oder nicht reagierende Programm Daten zu speichern, damit der Testcomputer für weitere Tests verwendet werden kann. Der Visual Studio-Debugger kann Dumpdateien für verwalteten oder systemeigenen Code speichern. Der Debugger kann Dumpdateien laden, die von Visual Studio oder von anderen Programmen erstellt wurden, die Dateien im *Minidump* -Format speichern.  
  
 ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> Dumpdateien, mit oder ohne Heaps  
 Sie können Dumpdateien mit oder ohne Heapinformationen erstellen.  
  
- **Dumpdateien mit Heaps** enthalten eine Momentaufnahme des Arbeitsspeichers der app. Dies umfasst die Werte der Variablen zum Zeitpunkt der Dumperstellung. Wenn Sie eine mit Heaps gespeicherte Dumpdatei laden, können die Symbole in Visual Studio geladen werden, auch wenn die Binärdateien der Anwendung nicht gefunden werden. Visual Studio speichert auch die Binärdateien der geladenen systemeigenen Module in der Dumpdatei, wodurch das Debugging wesentlich vereinfacht wird.  
  
- **Dumpdateien ohne Heaps** sind viel kleiner als Abbilder mit Heap Informationen. Allerdings muss der Debugger die Binärdateien der Anwendung laden, um die Symbolinformationen zu finden. Die Binärdateien müssen exakt mit den Binärdateien übereinstimmen, die für die Erstellung der Dumpdatei verwendet wurden. In den Dumpdateien ohne Heapdaten werden nur die Werte von Stapelvariablen gespeichert.  
  
  ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Anforderungen und Einschränkungen  
  
- Das Debuggen von Dumpdateien mit optimiertem Code kann unübersichtlich sein. Beispielsweise kann das Compiler-Inlining von Funktionen unerwartete Aufruflisten ergeben, und andere Optimierungen könnten die Lebensdauer der Variablen beeinflussen.  
  
- Dumpdateien von 64-Bit-Computern müssen auf einer Instanz von Visual Studio debuggt werden, das auf einem 64-Bit-Computer ausgeführt wird.  
  
- In Visual Studio-Versionen vor Visual Studio 2013 konnten Dumps von 32-Bit-Apps, die auf 64-Bit-Computern ausgeführt und mit einigen Tools erfasst wurden (z. B. Task-Manager und 64-Bit WinDbg), nicht in Visual Studio geöffnet werden. Diese Einschränkung wurde in Visual Studio 2013 aufgehoben.  
  
- Visual Studio kann Dumpdateien systemeigener Anwendungen von ARM-Geräten debuggen. Visual Studio kann auch Dumpdateien verwalteter Anwendungen von ARM-Geräten debuggen, jedoch nur im systemeigenen Debugger.  
  
- Zum Debuggen von Dumpdateien im [Kernel Modus](https://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) in Visual Studio 2013 laden Sie die [Windows 8.1-Version der Debugtools für Windows](https://msdn.microsoft.com/windows/hardware/gg463009)herunter. Weitere Informationen finden Sie [unter Kernel Debugging in Visual Studio](https://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
- Visual Studio kann keine Dumpdateien Debuggen, die im älteren dumpformat gespeichert sind, das als [vollständiges benutzermodusdump](/windows-hardware/drivers/debugger/user-mode-dump-files#full)bezeichnet wird Beachten Sie, dass ein vollständiger Benutzermodusdump nicht mit einer Dumpdatei mit Heapinformationen identisch ist.  
  
- Zum Debuggen mit dem [SOS.dll (SOS-Debugerweiterung)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498) in Visual Studio müssen Sie die Debugtools für Windows installieren, die Bestandteil des Windows Driver Kit (WDK) sind. Weitere Informationen finden [Sie unter Windows 8.1 Preview: Herunterladen von Kits, Bits und Tools](https://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
  ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Erstellen einer Dumpdatei  
 So erstellen Sie eine Dumpdatei mit Visual Studio  
  
- Beim Debuggen eines Prozesses in Visual Studio können Sie eine Dumpdatei speichern, wenn der Debugger an einer Ausnahme oder an einem Haltepunkt angehalten wurde. Wählen Sie **Dump speichern**unter, **Debuggen**aus. Im Dialogfeld **Dump speichern** unter können Sie in der Liste **Dateityp** die Option **Minidump** oder **Minidump mit Heap** (Standard) auswählen.  
  
- [Wenn Just-in-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md) aktiviert ist, können Sie den Debugger an einen abgestürzten Prozess anfügen, der außerhalb des Debuggers ausgeführt wird, und dann eine Dumpdatei speichern. Siehe [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
  Dumpdateien können auch mit jedem Programm erstellt werden, das das Windows-Minidumpformat unterstützt. Beispielsweise können mit dem Befehlszeilenprogramm **procdump** von [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) Prozess Absturz Abbild Dateien auf der Grundlage von Triggern oder Bedarfs gesteuert erstellt werden. Weitere Informationen zur Verwendung anderer Tools zum Erstellen von Dumpdateien finden Sie unter [Anforderungen und Einschränkungen](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) in diesem Thema.  
  
  ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Öffnen einer Dumpdatei  
  
1. Klicken Sie in Visual Studio auf **Datei**, **Öffnen**, **Datei**.  
  
2. Wählen Sie im Dialogfeld **Datei öffnen** die Dumpdatei aus. Die Dateierweiterung lautet in der Regel .dmp. Klicken Sie anschließend auf **Weiter**.  
  
3. Das Fenster zum Zusammenfassen der **Dumpdatei** wird angezeigt. In diesem Fenster können Sie Debug-Zusammenfassungsinformationen für die Dumpdatei anzeigen, den Symbolpfad festlegen, den Debugvorgang starten und die Zusammenfassungsinformationen in die Zwischenablage kopieren.  
  
     ![Minidump-Zusammenfassungsseite](../debugger/media/dbg-dump-summarypage.png "DBG_DUMP_SummaryPage")  
  
4. Wechseln Sie zum Starten des Debuggens zum Abschnitt **Aktionen** , und wählen Sie entweder **Debuggen mit nur native** oder **Debuggen mit Mixed**aus.  
  
## <a name="find-binaries-symbol-pdb-files-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Suchen von Binärdateien, Symbol Dateien (. pdb) und Quelldateien  
 Um die vollständigen Funktionen von Visual Studio zum Debuggen von Dumpdateien zu nutzen, benötigen Sie Zugriff auf die folgenden Dateien:  
  
- Die EXE-Datei, für die der Dump erstellt wurde, sowie andere Binärdateien (DLLs, usw.), die im Dumpprozess verwendet wurden.  
  
   Wenn Sie eine Dumpdatei mit Heapdaten debuggen, kann Visual Studio mit fehlenden Binärdateien für einige Module umgehen, es müssen jedoch Binärdateien für genügend Module vorhanden sein, um gültige Aufruflisten generieren zu können. Visual Studio schließt die systemeigenen Module in einer Dumpdatei mit Heapinformationen ein.  
  
- Symboldateien (PDB-Dateien) für die EXE-Datei und andere Binärdateien.  
  
- Quelldateien für die Module, die Sie interessieren.  
  
   Die ausführbaren Dateien und die PDB-Dateien müssen exakt mit der Version und dem Build der Dateien übereinstimmen, die für die Erstellung der Dumpdatei verwendet wurden.  
  
   Sie können mithilfe der Disassemblys der Module debuggen, wenn Sie die Quelldateien nicht finden können.  
  
  **Standardsuchpfade für ausführbare Dateien**  
  
  Visual Studio sucht automatisch diese Speicherorte für ausführbare Dateien, die nicht in der Dumpdatei enthalten sind:  
  
1. Das Verzeichnis mit der Dumpdatei.  
  
2. Der Pfad des Moduls, der in der Dumpdatei angegeben ist. Dies ist der Modulpfad auf dem Computer, auf dem das Speicherabbild erfasst wurde.  
  
3. Die Symbol Pfade, die im Dialogfeld Visual Studio- **Tools**, **Optionen** auf der Seite **Debuggen**, **Optionen**, **Symbole** angegeben sind. Sie können mehr Speicherorte für die Suche auf dieser Seite hinzufügen.  
  
   **Verwenden der Seite "Keine Binärdatei gefunden", "Keine Symbole gefunden", "Quelle nicht gefunden"**  
  
   Wenn Visual Studio die Dateien, die zum Debuggen eines Moduls im Dump benötigt werden, nicht finden kann, wird eine entsprechende Seite angezeigt (**keine Binärdatei gefunden**, **keine Symbole gefunden**oder **keine Quelle gefunden**). Diese Seiten enthalten ausführliche Informationen zu den Ursachen des Problems und stellen Aktionslinks bereit, mit denen Sie den richtigen Speicherort der Dateien identifizieren können. Weitere Informationen finden Sie unter [Angeben von Symbol-(PDB-) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
   ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Just-in-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Angeben von Symbol-(PDB-) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)
