---
title: Verwenden von Dumpdateien im Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/05/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b392cf5eddaab877af56ee952074cff646e10a59
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693450"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Dumpdateien in Visual Studio-debugger

<a name="BKMK_What_is_a_dump_file_"></a> Ein *Dumpdatei* ist eine Momentaufnahme, die anzeigt, den Prozess, die ausgeführt wurde und die Module, die für eine app zu einem bestimmten Zeitpunkt geladen wurden. Eine Dumpdatei mit Heapinformationen enthält auch eine Momentaufnahme des Speichers der Anwendung an diesem Punkt.

Öffnen einer Dumpdatei mit einem Heap in Visual Studio sieht in etwa folgendermaßen an einem Haltepunkt in einer Debugsitzung beenden. Obwohl die Ausführung fortgesetzt werden kann, können Sie den Stapel, Threads und Variablenwerte der app zum Zeitpunkt des Dumps überprüfen.

Dumpdateien werden hauptsächlich zum Debuggen von Problemen von Computern, die Entwickler haben keinen Zugriff auf. Sie können eine Dumpdatei vom Computer eines Kunden verwenden, wenn Sie kein Absturzes reproduzieren oder auf Ihrem eigenen Computer hängen. Tester können auch Dumpdateien um Absturz- oder blockierungsdaten zu sichern, verwenden Sie für weitere Tests erstellen.

Der Visual Studio-Debugger kann Dumpdateien für verwalteten oder systemeigenen Code speichern. Sie können debugdumpdateien erstellt Visual Studio oder andere apps, die Dateien im Speichern der *Minidump* Format.

##  <a name="BKMK_Requirements_and_limitations"></a> Anforderungen und Einschränkungen

-   Zum Debuggen von Dumpdateien von 64-Bit-Computern muss Visual Studio auf einem 64-Bit-Computer ausgeführt werden.

-   Visual Studio kann Dumpdateien systemeigener Anwendungen von ARM-Geräten debuggen. Sie können auch Dumpdateien von verwalteten Anwendungen von ARM-Geräten, jedoch nur in den systemeigenen Debugger Debuggen.

-   Zum Debuggen [im Kernelmodus](/windows-hardware/drivers/debugger/kernel-mode-dump-files) Dumpdateien, oder verwenden Sie die [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) Debugerweiterung in Visual Studio herunterladen Sie die Debugtools für Windows in der [Windows-Treiberkit (WDK)](/windows-hardware/drivers/download-the-wdk).

-   Visual Studio kann nicht die debugdumpdateien gespeichert, die im älteren, [vollständiger benutzermodusdump](/windows/desktop/wer/collecting-user-mode-dumps) Format. Ein vollständiger benutzermodusdump ist nicht mit einer Dumpdatei mit Heapinformationen identisch.

-   Das Debuggen von Dumpdateien mit optimiertem Code kann unübersichtlich sein. Beispielsweise kann das Compiler-Inlining von Funktionen unerwartete Aufruflisten ergeben, und andere Optimierungen könnten die Lebensdauer der Variablen beeinflussen.

##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Dumpdateien mit oder ohne Heaps

Dumpdateien können haben oder nicht Heapinformationen.

-   **Dumpdateien mit Heaps** enthalten eine Momentaufnahme des Speichers der Anwendung, einschließlich der Werte von Variablen, zum Zeitpunkt des Speicherabbilds. Visual Studio speichert auch die Binärdateien der geladenen systemeigenen Module in einer Dumpdatei mit einem Heap, wodurch das debugging wesentlich vereinfacht. Visual Studio kann aus einer Sicherungsdatei mit einem Heap auf Symbole laden, auch wenn eine app binäre nicht gefunden.

-   **Dumpdateien ohne Heaps** sind wesentlich kleiner als Dumpdateien mit Heaps, aber der Debugger muss geladen werden die Binärdateien der Anwendung um Symbolinformationen zu finden. Die geladenen Binärdateien müssen genau ausgeführt wird, während der Erstellung der Sicherung übereinstimmen. Dumpdateien ohne Heaps speichern Sie die Werte von Stapelvariablen nur.

##  <a name="BKMK_Create_a_dump_file"></a> Erstellen einer Dumpdatei

Während des Debuggens eines Prozesses in Visual Studio, können Sie ein Speicherabbild speichern, wenn der Debugger bei einer Ausnahme oder einem Haltepunkt beendet wurde.

Mit [Just-in-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md) aktiviert, Sie können Visual Studio-Debugger an einen abgestürzten Prozess außerhalb von Visual Studio Anfügen und speichern Sie eine Dumpdatei vom Debugger. Finden Sie unter [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**So speichern Sie eine Dumpdatei:**

1. Während bei einem Fehler oder einem Haltepunkt während des Debuggens angehalten wird, wählen Sie **Debuggen** > **Dump speichern unter**.

1. In der **Dump speichern unter** Dialogfeld **Dateityp**Option **Minidump** oder **Minidump mit Heap** (Standard).

1. Navigieren Sie zu einem Pfad, und wählen Sie einen Namen für die Dumpdatei, und wählen Sie dann **speichern**.

>[!NOTE]
>Sie können Dumpdateien mit jedem Programm erstellen, die die Windows-minidumpformat unterstützt. Beispielsweise können mit dem **Procdump**-Befehlszeilenhilfsprogramm von [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) Dumpdateien zu Prozessabstürzen anhand von Triggern oder bedarfsabhängig erstellt werden. Finden Sie unter [Anforderungen und Einschränkungen](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) Informationen zur Verwendung anderer Tools zum Erstellen von Dumpdateien.

##  <a name="BKMK_Open_a_dump_file"></a> Öffnen einer Dumpdatei

1. Wählen Sie in Visual Studio **Datei** > **öffnen** > **Datei**.

1. Wählen Sie im Dialogfeld **Datei öffnen** die Dumpdatei aus. Die Dateierweiterung lautet in der Regel *DMP*. Klicken Sie auf **OK**.

   Die **Minidump-Datei Zusammenfassung** Fenster zeigt die Zusammenfassung und das Modul Informationen für die Speicherabbilddatei und Aktionen können.

   ![Minidump-Zusammenfassungsseite](../debugger/media/dbg_dump_summarypage.png "Minidump-Zusammenfassungsseite")

1. Klicken Sie unter **Aktionen**:
   - Um das Laden der Speicherorte der Symbole festzulegen, wählen Sie **Symbolpfade festlegen**.
   - Wählen Sie zum Starten des Debuggens **Debuggen mit nur verwaltet**, **Debuggen von ausschließlich nativem Code**, **Debuggen von gemischtem Code**, oder **mit verwalteten Speicher Debuggen**.

##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Suchen von .exe, PDB und Quelldateien

Benötigt vollständige Debugfeatures auf eine Dumpdatei und Verwendung von Visual Studio:

- Die *.exe* Datei, die für die Sicherung erstellt wurde und andere Binärdateien (DLLs, usw.), die der dumpprozess verwendet.
- Symboldateien (*PDB*-Dateien) für die *EXE*-Datei und andere Binärdateien.
- Die *.exe* und *PDB* Erstellung zum Sichern von Dateien, die genau die Version und der Dateien an.
- Die Quelldateien für die relevanten Module. Sie können der disassemblys der Module verwenden, wenn Sie die Quelldateien nicht finden.

Wenn das Speicherabbild Heapdaten enthält, stellt Visual Studio mit fehlenden Binärdateien für einige Module, es müssen jedoch Binärdateien für ausreichend Module zum Generieren gültiger Aufruflisten.

### <a name="search-paths-for-exe-files"></a>Suchpfade für .exe-Dateien

Visual Studio sucht automatisch diese Speicherorte für *.exe* Dateien, die nicht in der Dumpdatei enthalten sind:

1. Der Ordner, der die Sicherungsdatei enthält.
2. Der Modulpfad gibt die Dumpdatei, der der Modulpfad auf dem Computer, der das Speicherabbild erfasst.
3. Die Symbolpfade, die im angegebenen **Tools** (oder **Debuggen**) > **Optionen** > **Debuggen**  >  **Symbole**. Sie können auch öffnen, die **Symbole** Seite die **Aktionen** im Bereich der **Zusammenfassung der Minidump-Datei** Fenster. Auf dieser Seite können Sie mehr Speicherorte für die Suche hinzufügen.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Verwenden Sie die Seiten keine binären, keine Symbole geladen oder Quelle nicht gefunden

Wenn Visual Studio die Dateien nicht finden können, muss zum Debuggen eines Moduls im Dump, es zeigt eine **keine Binärdatei gefunden**, **keine Symbole gefunden**, oder **Quelle nicht gefunden** Seite. Diese Seiten enthalten ausführliche Informationen zur Ursache des Problems, und geben Sie, dass die Aktionslinks, mit die Sie können die Dateien zu suchen. Weitere Informationen finden Sie unter [Angeben von Symbol- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Siehe auch

- [Just-In-Time debugging (Just-In-Time-Debuggen)](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Specify symbol (.pdb) and source files (Angeben von Symboldateien (PDB) und Quelldateien)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)