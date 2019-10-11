---
title: Clang-Projekteigenschaften (Android C++) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.EnableFunctionLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.FloatABI
- VC.Project.VCClangCompilerTool.BufferSecurityCheck
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.UseShortEnums
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.PrecompiledHeader
- VC.Project.VCClangCompilerTool.PrecompiledHeaderFile
- VC.Project.VCClangCompilerTool.PrecompiledHeaderOutputFileDirectory
- VC.Project.VCClangCompilerTool.PrecompiledHeaderCompileAs
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- VC.Project.VCClangCompilerTool.MultiProcessorCompilation
- vc.project.AdditionalOptionsPage
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 7c64ccedaeb8c13e353daaba0aeec0a388885bdf
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950655"
---
# <a name="clang-project-properties-android-c"></a>Clang-Projekteigenschaften (Android C++)

Eigenschaft | BESCHREIBUNG | Auswahlmöglichkeiten
--- | ---| ---
Zusätzliche Includeverzeichnisse | Gibt mindestens ein Verzeichnis an, das dem include-Pfad hinzugefügt werden soll. Verwenden Sie Semikolons als Trennzeichen, wenn mehrere Verzeichnisse vorhanden sind. (-I[path]).
Debuginformationsformat | Gibt den Typ der Debuginformationen an, die vom Compiler generiert werden. | **Keine**: Generiert keine Debuginformationen, sodass die Kompilierung ggf. schneller erfolgt.<br>**Vollständige Debugging-Informationen(DWARF2)** : Generiert DWARF2-Debuginformationen.<br>**Informationen zur Zeilennummer**: Nur Zeilennummerninformationen generieren.<br>
Name der Objektdatei | Gibt einen Namen an, um den Standardnamen der Objektdatei zu überschreiben. Dies kann ein Datei- oder Verzeichnisname sein. (/Fo[name]).
Warnstufe | Wählen Sie aus, wie streng der Compiler bei Codefehlern sein soll.  Andere Kennzeichnungen sollten direkt zu den zusätzlichen Optionen hinzugefügt werden. (/w, /Weverything). | **Alle Warnungen deaktivieren**: Deaktiviert alle Compilerwarnungen.<br>**Alle Warnungen aktivieren**: Aktiviert alle Warnungen, einschließlich standardmäßig deaktivierter Warnungen.<br>
Warnungen als Fehler behandeln | Behandelt alle Compilerwarnungen als Fehler. Bei einem neuen Projekt kann es empfehlenswert sein, /WX in allen Kompilierungen zu verwenden. Das Beheben aller Warnungen stellt sicher, dass die geringstmögliche Anzahl schwer zu findender Codefehler vorhanden ist.
Ausführlichen Modus aktivieren | Befehle zum Ausführen und Verwenden der ausführlichen Ausgabe anzeigen.
Optimierung | Gibt die Optimierungsstufe für die Anwendung an. | **Benutzerdefiniert**: Benutzerdefinierte Optimierung<br>**Deaktiviert**: Deaktivieren der Optimierung.<br>**Größe minimieren**: Größenoptimierung<br>**Geschwindigkeit maximieren**: Geschwindigkeitsoptimierung<br>**Vollständige Optimierung**: teure Optimierungen<br>
Strenges Aliasing | Annehmen der strengsten Aliasingregeln.  Bei einem Objekt eines Typs wird niemals davon ausgegangen, dass es sich an derselben Adresse wie ein Objekt eines anderen Typs befindet.
Framezeiger unterdrücken | Unterdrückt die Erstellung von Framezeigern im Anrufstapel.
C++-Ausnahmen aktivieren | Gibt das Ausnahmebehandlungsmodell an, das vom Compiler verwendet wird. | **Nein**: Ausnahmebehandlung deaktivieren.<br>**Ja**: Ausnahmebehandlung aktivieren.<br>**Entladetabellen**: Alle erforderlichen statischen Daten werden generiert. Das hat jedoch keine Auswirkungen auf den generierten Code.<br>
Funktionslevel-Linking aktivieren | Ermöglicht dem Compiler, einzelne Funktionen in Form von kompilierten Funktionen (COMDATs) zu kompilieren. Zur Bearbeitung erforderlich, funktionieren weiterhin.     (ffunction-sections).
Datenlevel-Linking aktivieren | Ermöglicht Linker-Optimierungen, nicht verwendete Daten zu entfernen, indem jedes Datenelement in einem separaten Feld ausgegeben wird.
Advanced SIMD (Neon) aktivieren | Aktiviert die Codegenerierung für NEON-Gleitkomma-Hardware. Dies gilt nur für die ARM-Architektur.
Gleitkomma-ABI | Wählen Sie eine Option aus, um die Gleitkomma-ABI auszuwählen. | **Soft**: „Soft“ sorgt dafür, dass der Compiler eine Ausgabe mit Bibliotheksaufrufen für Gleitkommavorgänge generiert.<br>**SoftFP**: „SoftFP“ ermöglicht die Generierung von Code unter Verwendung von Gleitkommahardware-Anweisungen, verwendet jedoch weiterhin die Konventionen für den soft-float-Aufruf.<br>**Hard**: „Hard“ ermöglicht die Generierung von Gleitkomma-Anweisungen und verwendet FPU-spezifische Aufrufkonventionen.<br>
Sicherheitsüberprüfung | Die Sicherheitsprüfung hilft bei der Erkennung von Überläufen des Stapelpuffers. Hierbei handelt es sich um gängige Versuche, die Sicherheit eines Programms zu gefährden. (fstack-protector). | **Sicherheitsüberprüfung deaktivieren**: Sicherheitsüberprüfung deaktivieren.<br>**Sicherheitsüberprüfung aktivieren**: Sicherheitsüberprüfung aktivieren. (fstack-protector).<br>
Positionsunabhängiger Code | Generieren von positionsunabhängigem Code (Position Independent Code, PIC) für die Verwendung in einer freigegebenen Bibliothek.
Kurze Enumerationen verwenden | Dieser Enumerationstyp verwendet nur so viele Bytes, wie das Eingabeset an möglichen Werten erfordert.
Laufzeit-Typeninformation aktivieren | Fügt Code für die Überprüfung der C++-Objekttypen während der Laufzeit hinzu (Laufzeit-Typinformationen).     (frtti, fno-rtti)
C-Sprachstandard | Bestimmt den C-Sprachstandard. | **Default**<br>**C89**: C89-Sprachstandard.<br>**C99**: C99-Sprachstandard.<br>**C11**: C11-Sprachstandard.<br>**C99 (GNU-Dialekt)** : C99-Sprachstandard (GNU-Dialekt).<br>**C11 (GNU-Dialekt)** : C11-Sprachstandard (GNU-Dialekt).<br>
C++-Sprachstandard | Bestimmt den C++-Sprachstandard | **Default**<br>**C++03**: C++03-Sprachstandard.<br>**C++11**: C++11-Sprachstandard.<br>**C++14**: C++14-Sprachstandard.<br>**C++03 (GNU-Dialekt)** : C++03-Sprachstandard (GNU-Dialekt).<br>**C++11 (GNU-Dialekt)** : C++11-Sprachstandard (GNU-Dialekt).<br>**C++14 (GNU-Dialekt)** : C++14-Sprachstandard (GNU-Dialekt).<br>
Präprozessordefinitionen | Definiert Präprozessorsymbole für Ihre Quelldatei. (-D)
Präprozessordefinitionen aufheben | Gibt mindestens eine aufgehobene Präprozessordefinition an.  (-U [macro])
Alle Präprozessordefinitionen aufheben | Hebt die Definition aller zuvor definierten Präprozessorwerte auf.  (-undef)
Includedateien anzeigen | Generiert eine Liste der Includedateien mit Compilerausgabe.  (-H)
Vorkompilierter Header | Vorkompilierten Header erstellen/verwenden: Ermöglicht die Erstellung oder Verwendung eines vorkompilierten Headers während der Erstellung. | **Verwenden**: Vorkompilierten Header verwenden.<br>**Vorkompilierte Header nicht verwenden**: Vorkompilierten Header nicht verwenden.<br>
Vorkompilierte Headerdatei | Gibt den Namen einer Headerdatei an, die als vorkompilierte Headerdatei verwendet werden soll. Diese Datei wird während des Erstellungsvorgangs auch zu „Explizite Includedateien“ hinzugefügt.
Ausgabedateiverzeichnis für vorkompilierte Header | Gibt das Verzeichnis für den generierten vorkompilierten Header an. Dieses Verzeichnis wird während des Erstellungsvorgangs auch zu „Zusätzliche Includeverzeichnisse“ hinzugefügt.
Vorkompilierten Header kompilieren: Optionen | Wählen Sie „Kompilierungssprachenoption für vorkompilierte Headerdatei (-x c-Header, -x c++-Header)“ aus. | **Als C-Code kompilieren**: als C-Code kompilieren.<br>**Als C++-Code kompilieren**: als C++-Code kompilieren.<br>
Kompilieren als | Wählen Sie die Kompilierungssprachenoption für C- und CPP-Dateien aus.  „Standard“ führt die Erkennung basierend auf der .c- oder .cpp-Dateierweiterung aus. (-x c, -x c++) | **Standard**: die Standardeinstellung.<br>**Als C-Code kompilieren**: als C-Code kompilieren.<br>**Als C++-Code kompilieren**: als C++-Code kompilieren.<br>
Explizite Includedateien | eine oder mehrere explizite Includedateien.     (-include [name])
Kompilierung mit mehreren Prozessoren | Kompilierung mit mehreren Prozessoren
Zusätzliche Optionen | Zusätzliche Optionen.
