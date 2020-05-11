---
title: Unterstützte Code ÄnderungenC++() | Microsoft-Dokumentation
ms.date: 02/18/2020
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: af6c0d88dd230bee768641905e200f1f47749d77
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77629585"
---
# <a name="supported-code-changes-c"></a>Unterstützte Codeänderungen (C++)
"Bearbeiten und fort C++ fahren" für Projekte behandelt die meisten Arten von Codeänderungen. Einige Änderungen können während der Programmausführung jedoch nicht übernommen werden. Um diese Änderungen zu übernehmen, müssen Sie die Ausführung anhalten und eine neue Version des Codes erstellen.

 Weitere Informationen zum Arbeiten mit "Bearbeiten und Fortfahren" C++ in Visual Studio finden Sie unter " [Bearbeiten und Fortfahren" (C++)](../debugger/edit-and-continue-visual-cpp.md) .

## <a name="BKMK_Requirements"></a> Anforderungen
### <a name="build-settings-project--properties"></a>Buildeinstellungen (Eigenschaften von Project >):
  1. **C/C++ > Allgemein > Debuginformationsformat**: Programmdatenbank zum Bearbeiten und Fortfahren (`/ZI`)
  2. **C/C++ >-Code Generierung > minimale Neuerstellung aktivieren**: Ja (`/Gm`)
  3. **Linker > Allgemein > inkrementelle Verknüpfung aktivieren**: Ja (`/INCREMENTAL`)

     Alle nicht kompatiblen Linker-Einstellungen (z. b. `/SAFESEH`oder `/OPT:`...) sollten während des Builds eine Warnung _LNK4075_ verursachen.  
     Beispiel: `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>Debugger-Einstellungen (debug > Optionen > Allgemein):
  - Systemeigenes Bearbeiten und Fortfahren aktivieren

     Alle nicht kompatiblen Compilereinstellungen oder Linkereinstellungen verursachen beim Bearbeiten und Fortfahren einen Fehler.  
     Beispiel: `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="BKMK_Unsupported_changes"></a> Nicht unterstützte Änderungen
 Die folgenden C/C++ -Änderungen können während einer Debugsitzung nicht angewendet werden. Wenn Sie eine dieser Änderungen vornehmen und anschließend versuchen, Codeänderungen zu übernehmen, wird im **Ausgabe** Fenster eine Fehler-oder Warnmeldung angezeigt.

- Die meisten Änderungen an globalen oder statischen Daten.

- Änderungen an ausführbaren Dateien, die von einem anderen Computer kopiert und nicht lokal erstellt wurden.

- Änderungen an Datentypen, die das Layout eines Objekts beeinflussen (z. B. Datenmember einer Klasse).

- Hinzufügen von mehr als 64 KB neuen Codes oder neuer Daten.

- Hinzufügen von Variablen, die an einer Stelle vor dem Anweisungszeiger einen Konstruktor benötigen.

- Änderungen, die sich auf Code auswirken, der eine Laufzeitinitialisierung benötigt.

- Das Hinzufügen von Ausnahmehandlern in bestimmten Instanzen.

- Änderungen an Ressourcendateien.

- Änderungen an Code in schreibgeschützten Dateien.

- Änderungen am Code ohne entsprechende PDB-Datei.

- Änderungen an Code ohne Objektdatei.

* Ändern von Lambdas:
  - Einen statischen oder globalen Member haben.
  - Werden an eine Std:: function-Funktion übermittelt. Dies verursacht eine echte ODR-Verletzung und Ergebnisse in C1092.

- Von "Bearbeiten und Fortfahren" werden keine statischen Bibliotheken aktualisiert. Wenn Sie eine Änderung an einer statischen Bibliothek vornehmen, wird die Ausführung ohne Warnung mit der alten Version fortgeführt.

## <a name="BKMK_Unsupported_scenarios"></a> Nicht unterstützte Szenarien
 "Bearbeiten und Fortfahren" steht für C/C++ in den folgenden Debugszenarien nicht zur Verfügung:

- Debuggen von systemeigenen Apps, die mit [/zo (Optimiertes Debuggen verbessern)](/cpp/build/reference/zo-enhance-optimized-debugging)kompiliert sind

- In Versionen von Visual Studio vor Visual Studio 2015 Update 1, Debuggen von UWP-Apps oder-Komponenten. Ab Visual Studio 2015 Update 1 können Sie "Bearbeiten und Fortfahren" in UWP C++ -apps und DirectX-Apps verwenden, da jetzt der `/ZI`-Compilerschalter mit dem `/bigobj`-Schalter unterstützt wird. Sie können „Bearbeiten und Fortfahren“ auch mit Binärdateien verwenden, die mit dem `/FASTLINK` -Schalter unterstützt wird.

- Debuggen von 8/8.1-Store-Apps. In diesen Projekten werden das Toolset VC 120 und der SchalterC++ C/`/bigobj` verwendet. "Bearbeiten und Fortfahren" mit `/bigobj` wird nur im VC 140-Toolset unterstützt.

- Debuggen unter Windows 98.

- Debuggen im gemischten Modus (systemeigen/verwaltet).

- JavaScript-Debugging.

- SQL-Debuggen.

- Debuggen einer Dumpdatei.

- Bearbeiten von Code nach einer nicht behandelten Ausnahme, wenn die Option **Aufrufliste für unbehandelte Ausnahmen entladen** nicht aktiviert ist.

- Debuggen einer App über **Anfügen an** , anstatt die App durch Auswählen von **Start** im Menü **Debuggen** auszuführen.

- Debuggen von optimiertem Code.

- Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.

- Verwenden eines benutzerdefinierten compilerpfads (*cl. exe*). Aus Sicherheitsgründen wird bei der erneuten Kompilierung einer Datei während "Bearbeiten und Fortfahren" der installierte Compiler immer von Visual Studio verwendet. Wenn Sie einen benutzerdefinierten compilerpfad verwenden (z. b. über eine benutzerdefinierte `$(ExecutablePath)` Variable in der `*.props` Datei), wird eine Warnung angezeigt, und Visual Studio greift auf den installierten Compiler derselben Version bzw. Architektur zurück.

- FastBuild-Buildsystem. FastBuild ist zurzeit nicht kompatibel mit dem Compilerschalter "Enable Minimum Rebuild (`/Gm`)", sodass "Bearbeiten und Fortfahren" nicht unterstützt wird.

- Legacy Architekturen/VC-Toolsets. Beim VC 140-Toolset unterstützt der Standard Debugger das Bearbeiten und Fortfahren mit x86-und x64-Anwendungen. Legacy-Toolsets unterstützen nur x86-Anwendungen. Toolsets, die älter als VC 120 sind, sollten den Legacy Debugger verwenden, indem Sie "_debug > Optionen > Allgemeine >_ systemeigenen Kompatibilitätsmodus verwenden" aktivieren, um "Bearbeiten und Fortfahren" zu verwenden.

## <a name="BKMK_Linking_limitations"></a> Einschränkungen für Verknüpfungen

### <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Optionen des Linkers, durch die "Bearbeiten und Fortfahren" deaktiviert wird
 Die folgenden Optionen des Linkers deaktivieren Bearbeiten und Fortfahren:

- Durch die Einstellung **/OPT:REF**, **/OPT:ICF**oder **/INCREMENTAL:NO** wird Bearbeiten und Fortfahren deaktiviert. Folgende Warnung wird angezeigt:  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- Wenn Sie **/Order**, **/Release**oder **/Force** festlegen, wird bearbeiten und Fortfahren deaktiviert. folgende Warnung wird angezeigt:  
     `LINK : warning LNK4075: ignoring /INCREMENTAL due to /option specification`

- Durch das Festlegen einer beliebigen Option, die die Erstellung einer Programmdatenbankdatei (.pdb) verhindert, wird Bearbeiten und Fortfahren deaktiviert, wobei keine spezifische Warnung ausgegeben wird.

### <a name="BKMK_Auto_relinking_limitations"></a> Automatisches Neuverknüpfen von Einschränkungen
 In der Standardeinstellung wird durch Bearbeiten und Fortfahren das Programm am Ende der Debugsitzung neu gebunden, um eine aktuelle ausführbare Datei zu erstellen.

 Bearbeiten und Fortfahren kann das Programm nicht erneut binden, wenn Sie an einer anderen Position als der der ursprünglichen Erstellung debuggen. Ihnen wird in einer Meldung mitgeteilt, dass Sie manuell neu erstellen müssen.

 Bearbeiten und Fortfahren erstellt keine statischen Bibliotheken neu. Wenn Sie eine statische Bibliothek mit "Bearbeiten und Fortfahren" ändern, müssen Sie die Bibliothek manuell neu erstellen und die Apps anschließend mit der neuen Bibliothek erneut verknüpfen.

 Durch Bearbeiten und Fortfahren können keine benutzerdefinierten Schritte aufgerufen werden. Wenn das Programm auf benutzerdefinierten Buildschritten beruht, können Sie es manuell neu erstellen, damit benutzerdefinierte Buildschritte aufgerufen werden können. In diesem Fall können Sie die erneute Bindung nach Ausführen von Bearbeiten und Fortfahren deaktivieren. Dies gewährleistet, dass Sie aufgefordert werden, diese manuell neu zu erstellen.

 **So deaktivieren Sie das erneute Binden nach "Bearbeiten und Fortfahren"**

1. Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**.

2. Öffnen Sie im Dialogfeld **Optionen** den Knoten **Debugging** , und wählen Sie den Knoten **Bearbeiten und Fortfahren** aus.

3. Deaktivieren Sie das Kontrollkästchen **Codeänderungen nach dem Debuggen erneut binden** .

## <a name="BKMK_Precompiled_header_limitations"></a>Einschränkungen für vorkompilierte Header
 Durch Bearbeiten und Fortfahren werden vorkompilierte Header standardmäßig im Hintergrund geladen und verarbeitet, um die Verarbeitung von Codeänderungen zu beschleunigen. Zum Laden vorkompilierter Header muss physischer Speicher belegt werden. Daher können beim Kompilieren auf einem Computer mit begrenztem Arbeitsspeicher Probleme auftreten. Sie können feststellen, ob möglicherweise ein solches Problem besteht, indem Sie mithilfe des Windows Task-Managers den während des Debuggens verfügbaren physischen Speicher bestimmen. Wenn dabei die Größe der vorkompilierten Header überschritten wird, kann Bearbeiten und Fortfahren problemlos ausgeführt werden. Wenn der Speicherplatz geringer als die vorkompilierten Header ist, können Sie das Laden von vorkompilierten Headern im Hintergrund durch Bearbeiten und Fortfahren verhindern.

 **So deaktivieren Sie das Laden vorkompilierter Header im Hintergrund für "Bearbeiten und Fortfahren"**

1. Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**.

2. Öffnen Sie im Dialogfeld **Optionen** den Knoten **Debugging** , und wählen Sie den Knoten **Bearbeiten und Fortfahren** aus.

3. Deaktivieren Sie das Kontrollkästchen **Präkompilierung zulassen** .

## <a name="BKMK_IDL_attribute_limitations"></a>Einschränkungen für IDL-Attribute
 "Bearbeiten und Fortfahren" unterstützt nicht das Neugenerieren von IDL-Dateien (Interface Definiton Language). Aus diesem Grund werden Änderungen an IDL-Attributen während des Debuggens nicht widergespiegelt. Wenn Sie die Ergebnisse von Änderungen an IDL-Attributen anzeigen möchten, müssen Sie das Debuggen beenden und die App neu erstellen. "Bearbeiten und Fortfahren" erzeugt keinen Fehler bzw. keine Fehlermeldung, wenn IDL-Attribute geändert wurden. Weitere Informationen finden Sie unter [IDL-Attribute](/cpp/windows/idl-attributes).

## <a name="BKMK_Diagnosing_issues"></a>Diagnostizieren von Problemen
 Wenn Ihr Szenario keinen der oben genannten Bedingungen erfüllt, können Sie weitere Details erfassen, indem Sie den folgenden DWORD-Registrierungs Wert festlegen:
 1. Öffnen Sie eine Developer-Eingabeaufforderung.
 2. Führen Sie den folgenden Befehl aus:  
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`

 Das Festlegen dieses Werts zu Beginn einer Debugsitzung bewirkt, dass die verschiedenen Komponenten von "Bearbeiten und Fortfahren" die ausführliche Protokollierung im Bereich " **Ausgabefenster** > **Debuggen** ".

## <a name="see-also"></a>Siehe auch
- [Bearbeiten und FortfahrenC++()](../debugger/edit-and-continue-visual-cpp.md)
