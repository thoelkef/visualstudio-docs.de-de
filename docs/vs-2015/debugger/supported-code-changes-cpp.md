---
title: Unterstützte Codeänderungen (C++) | Microsoft-Dokumentation
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
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C# language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C#], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd4e1af62032920196dbd8171769f1dc079324e8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225354"
---
# <a name="supported-code-changes-c"></a>Unterstützte Codeänderungen (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit "Bearbeiten und Fortfahren" für Visual C++ können die meisten Arten von Codeänderungen behandelt werden. Einige Änderungen können während der Programmausführung jedoch nicht übernommen werden. Um diese Änderungen zu übernehmen, müssen Sie die Ausführung anhalten und eine neue Version des Codes erstellen.  
  
 Weitere Informationen zum Arbeiten mit „Bearbeiten und Fortfahren“ für C++ in Visual Studio finden Sie unter [Edit and Continue (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) .  
  
##  <a name="BKMK_Unsupported_changes"></a> Nicht unterstützte Änderungen  
 Folgende Änderungen an C-/C++-Code können während einer Debugsitzung nicht übernommen werden:  
  
-   Die meisten Änderungen an globalen oder statischen Daten.  
  
-   Änderungen an ausführbaren Dateien, die von einem anderen Computer kopiert und nicht lokal erstellt wurden.  
  
-   Änderungen an Datentypen, die das Layout eines Objekts beeinflussen (z. B. Datenmember einer Klasse).  
  
-   Hinzufügen von mehr als 64 KB neuen Codes oder neuer Daten.  
  
-   Hinzufügen von Variablen, die an einer Stelle vor dem Anweisungszeiger einen Konstruktor benötigen.  
  
-   Änderungen, die sich auf Code auswirken, der eine Laufzeitinitialisierung benötigt.  
  
-   Das Hinzufügen von Ausnahmehandlern in bestimmten Instanzen.  
  
-   Änderungen an Ressourcendateien.  
  
-   Änderungen an Code in schreibgeschützten Dateien.  
  
-   Änderungen am Code ohne entsprechende PDB-Datei.  
  
-   Änderungen an Code ohne Objektdatei.  
  
 Wenn Sie eine dieser Änderungen vornehmen und anschließend versuchen, die Codeänderungen zu übernehmen, wird im Fenster **Ausgabe** eine Warnung oder eine Fehlermeldung angezeigt.  
  
-   Von "Bearbeiten und Fortfahren" werden keine statischen Bibliotheken aktualisiert. Wenn Sie eine Änderung an einer statischen Bibliothek vornehmen, wird die Ausführung ohne Warnung mit der alten Version fortgeführt.  
  
##  <a name="BKMK_Unsupported_scenarios"></a> Nicht unterstützte Szenarien  
 "Bearbeiten und Fortfahren" steht für C/C++ in den folgenden Debugszenarien nicht zur Verfügung:  
  
-   Debuggen von systemeigenen Apps, die mit [/zo (Optimiertes Debuggen verbessern)](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)kompiliert sind  
  
-   Debuggen von Windows Store-Apps oder -Komponenten in Versionen von Visual Studio vor Visual Studio 2015 Update 1 Ab Visual Studio 2015 Update 1 können Sie „Bearbeiten und Fortfahren“ in Windows Store C++- und DirectX-Apps verwenden, da jetzt der `/ZI` -Compilerschalter mit dem  `/bigobj` -Schalter unterstützt wird. Sie können „Bearbeiten und Fortfahren“ auch mit Binärdateien verwenden, die mit dem `/FASTLINK` -Schalter unterstützt wird.  
  
-   Debuggen unter Windows 98.  
  
-   Debuggen im gemischten Modus (systemeigen/verwaltet).  
  
-   Debuggen von JavaScript.  
  
-   SQL-Debuggen.  
  
-   Debuggen einer Dumpdatei.  
  
-   Bearbeiten von Code nach einer nicht behandelten Ausnahme, wenn die Option **Aufrufliste für unbehandelte Ausnahmen entladen** nicht aktiviert ist.  
  
-   Debuggen einer App über **Anfügen an** , anstatt die App durch Auswählen von **Start** im Menü **Debuggen** auszuführen.  
  
-   Debuggen von optimiertem Code.  
  
-   Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.  
  
##  <a name="BKMK_Linking_limitations"></a> Einschränkungen für Verknüpfungen  
  
###  <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Optionen des Linkers, durch die "Bearbeiten und Fortfahren" deaktiviert wird  
 Die folgenden Optionen des Linkers deaktivieren Bearbeiten und Fortfahren:  
  
-   Durch die Einstellung **/OPT:REF**, **/OPT:ICF**oder **/INCREMENTAL:NO** wird Bearbeiten und Fortfahren deaktiviert. Folgende Warnung wird angezeigt:  
  
     LINK : Warnung LNK4075: ignoriere /EDITANDCONTINUE aufgrund von /OPT  
  
     Angabe  
  
-   Durch die Einstellung von **/ORDER**, **/RELEASE**oder **/FORCE** wird Bearbeiten und Fortfahren deaktiviert. Folgende Warnung wird angezeigt:  
  
     LINK: Warnung LNK4075: /INCREMENTAL wird aufgrund von /option ignoriert  
  
     Angabe  
  
-   Durch das Festlegen einer beliebigen Option, die die Erstellung einer Programmdatenbankdatei (.pdb) verhindert, wird Bearbeiten und Fortfahren deaktiviert, wobei keine spezifische Warnung ausgegeben wird.  
  
###  <a name="BKMK_Auto_relinking_limitations"></a> Automatisches Neuverknüpfen von Einschränkungen  
 In der Standardeinstellung wird durch Bearbeiten und Fortfahren das Programm am Ende der Debugsitzung neu gebunden, um eine aktuelle ausführbare Datei zu erstellen.  
  
 Bearbeiten und Fortfahren kann das Programm nicht erneut binden, wenn Sie an einer anderen Position als der der ursprünglichen Erstellung debuggen. Ihnen wird in einer Meldung mitgeteilt, dass Sie manuell neu erstellen müssen.  
  
 Bearbeiten und Fortfahren erstellt keine statischen Bibliotheken neu. Wenn Sie eine statische Bibliothek mit "Bearbeiten und Fortfahren" ändern, müssen Sie die Bibliothek manuell neu erstellen und die Apps anschließend mit der neuen Bibliothek erneut verknüpfen.  
  
 Durch Bearbeiten und Fortfahren können keine benutzerdefinierten Schritte aufgerufen werden. Wenn das Programm auf benutzerdefinierten Buildschritten beruht, können Sie es manuell neu erstellen, damit benutzerdefinierte Buildschritte aufgerufen werden können. In diesem Fall können Sie die erneute Bindung nach Ausführen von Bearbeiten und Fortfahren deaktivieren. Dies gewährleistet, dass Sie aufgefordert werden, diese manuell neu zu erstellen.  
  
 **So deaktivieren Sie das erneute Binden nach "Bearbeiten und Fortfahren"**  
  
1.  Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**.  
  
2.  Öffnen Sie im Dialogfeld **Optionen** den Knoten **Debugging** , und wählen Sie den Knoten **Bearbeiten und Fortfahren** aus.  
  
3.  Deaktivieren Sie das Kontrollkästchen **Codeänderungen nach dem Debuggen erneut binden** .  
  
##  <a name="BKMK_Precompiled_Header_Limitations"></a> Einschränkungen für vorkompilierte Header  
 Durch Bearbeiten und Fortfahren werden vorkompilierte Header standardmäßig im Hintergrund geladen und verarbeitet, um die Verarbeitung von Codeänderungen zu beschleunigen. Zum Laden vorkompilierter Header muss physischer Speicher belegt werden. Daher können beim Kompilieren auf einem Computer mit begrenztem Arbeitsspeicher Probleme auftreten. Sie können feststellen, ob möglicherweise ein solches Problem besteht, indem Sie mithilfe des Windows Task-Managers den während des Debuggens verfügbaren physischen Speicher bestimmen. Wenn dabei die Größe der vorkompilierten Header überschritten wird, kann Bearbeiten und Fortfahren problemlos ausgeführt werden. Wenn der Speicherplatz geringer als die vorkompilierten Header ist, können Sie das Laden von vorkompilierten Headern im Hintergrund durch Bearbeiten und Fortfahren verhindern.  
  
 **So deaktivieren Sie das Laden vorkompilierter Header im Hintergrund für "Bearbeiten und Fortfahren"**  
  
1.  Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**.  
  
2.  Öffnen Sie im Dialogfeld **Optionen** den Knoten **Debugging** , und wählen Sie den Knoten **Bearbeiten und Fortfahren** aus.  
  
3.  Deaktivieren Sie das Kontrollkästchen **Präkompilierung zulassen** .  
  
##  <a name="BKMK_IDL_Attribute_Limitations"></a> Einschränkungen für IDL-Attribute  
 "Bearbeiten und Fortfahren" unterstützt nicht das Neugenerieren von IDL-Dateien (Interface Definiton Language). Aus diesem Grund werden Änderungen an IDL-Attributen während des Debuggens nicht widergespiegelt. Wenn Sie die Ergebnisse von Änderungen an IDL-Attributen anzeigen möchten, müssen Sie das Debuggen beenden und die App neu erstellen. "Bearbeiten und Fortfahren" erzeugt keinen Fehler bzw. keine Fehlermeldung, wenn IDL-Attribute geändert wurden. Weitere Informationen finden Sie unter [IDL-Attribute](http://msdn.microsoft.com/library/04c596f4-c97b-4952-8053-316678b1d0b6).  
  
## <a name="see-also"></a>Siehe auch  
 [Edit and Continue (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)



