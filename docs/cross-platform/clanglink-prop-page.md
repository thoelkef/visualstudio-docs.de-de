---
title: Clang-Linkereigenschaften (Android C++) | Microsoft-Dokumentation
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 2b4ca3f4c67315357343d1803bda12f11d8cbc6d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="clang-linker-properties-android-c"></a>Clang-Linkereigenschaften (Android C++)

Eigenschaft | description | Auswahlmöglichkeiten
--- | ---| ---
Ausgabedatei | Die Option überschreibt den Standardnamen und den Speicherort des Programms, das der Linker erstellt. (-o)
Status anzeigen | Gibt Linkerstatusmeldungen aus.
Version | Die Option -version weist den Linker an, eine Versionsnummer in den Header der ausführbaren Datei einzufügen.
Ausführliche Ausgabe aktivieren | Die Option -verbose weist den Linker an, ausführliche Meldungen zum Debuggen auszugeben.
Inkrementelle Verknüpfung aktivieren | Diese Option weist den Linker an, die inkrementelle Verknüpfung zu aktivieren.
Suchpfad freigegebene Bibliothek | Ermöglicht dem Benutzer, den Suchpfad für die freigegebene Bibliothek mit Daten aufzufüllen.
Zusätzliche Bibliotheksverzeichnisse | Ermöglicht dem Benutzer das Überschreiben des umgebungsbedingten Bibliothekspfads. (-L Ordner).
Nicht aufgelöste Symbolverweise melden | Wenn diese Option aktiviert ist, werden ungelöste Symbolverweise gemeldet.
Für Speicherverbrauch optimieren | Optimiert den Speicherverbrauch, indem die Symboltabellen bei Bedarf erneut gelesen werden.
Bestimmte Standardbibliotheken ignorieren | Gibt einen oder mehrere Namen der zu ignorierenden Standardbibliotheken an.
Symbolverweise erzwingen | Erzwingt, dass das Symbol als undefiniertes Symbol in die Ausgabedatei eingegeben wird.
Debuggersymbolinformationen | Debuggersymbolinformationen aus der Ausgabedatei. | **Alle einschließen**<br>**Nicht benötigte Symbole für Umsetzungsvorgänge auslassen**<br>**Nur Debuggersymbolinformationen auslassen**<br>**Alle Symbolinformationen auslassen**<br>
Debuggersymbolinformationen packen | Entfernen Sie die Debuggersymbolinformationen vor dem Packen.  Eine Kopie der ursprünglichen Binärdatei wird zum Debuggen verwendet.
Name der Zuordnungsdatei | Die Option Map weist den Linker an, eine Zuordnungsdatei mit dem vom Benutzer angegebenen Namen zu erstellen.
Variablen nach dem Umsetzen als ReadOnly kennzeichnen | Diese Option kennzeichnet Variablen nach dem Umsetzen als schreibgeschützt.
Sofortige Funktionsbindung aktivieren | Diese Option kennzeichnet das Objekt für sofortige Funktionsbindung.
Ausführbaren Stapel erfordern | Diese Option gibt an, dass die Ausgabe keinen ausführbaren Stapel erfordert.
Gesamtes Archiv | Diese Option verwendet den gesamten Code aus den Quellen und zusätzlichen Abhängigkeiten.
Zusätzliche Optionen | Zusätzliche Optionen.
Zusätzliche Abhängigkeiten | Gibt zusätzliche Elemente an, die der Linkerbefehlszeile hinzugefügt werden sollen.
Bibliothekabhängigkeiten | Mit dieser Option können zusätzliche Bibliotheken angegeben werden, die der Linkerbefehlszeile hinzugefügt werden sollen. Die zusätzlichen Bibliotheken werden am Ende der Linkerbefehlszeile hinzugefügt. Diese beginnen mit „lib“ und enden mit der Erweiterung „A“ oder „SO“.  (-lFILE)
