---
title: Allgemein, Debuggen, Dialogfeld "Optionen" | Microsoft Docs
ms.custom: ''
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b7af8c68764b3a9ed85bf6a52a3a6c4a0568203
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572049"
---
# <a name="general-debugging-options-dialog-box"></a>Allgemein, Debuggen, Dialogfeld "Optionen"
Die **Extras > Optionen > Debugging > Allgemein** Seite ermöglicht Ihnen das in diesem Artikel beschriebenen Optionen festlegen.

Wenn Sie die Standardeinstellungen wiederherstellen müssen, erreichen Sie, dass die Verwendung **Tools** > **Einstellungen importieren und exportieren** > **alle Einstellungen zurücksetzen**. Wenn Sie nur eine Teilmenge der Einstellungen zurücksetzen möchten, speichern Sie die Einstellungen in der **-Import / Export-Assistent** vornehmen der Änderungen, die Sie testen möchten, klicken Sie dann die gespeicherten Einstellungen später importieren.
  
**Vor dem Löschen aller Haltepunkte Fragen** erfordert eine Bestätigung vor dem Abschluss der **alle Breakpoints löschen** Befehl.  
  
**Alle Prozesse anhalten, wenn ein Prozess anhält** gleichzeitig hält alle Prozesse, die auf die der Debugger wird, angefügt, wenn eine Unterbrechung auftritt.  
  
**Überschreitenden Ausnahmen bei Anwendungsdomänengrenzen oder verwaltete/systemeigene unterbrechen** beim Debuggen im verwalteten oder gemischten Modus die common Language Runtime kann Ausnahmen auffangen, die cross Anwendungsdomänengrenzen oder verwaltete/systemeigene bei folgenden Bedingungen sind erfüllt:  
  
1\) bei systemeigenem Code verwalteter Code mit COM-Interop aufgerufen und der verwaltete Code löst eine Ausnahme aus. Finden Sie unter [Einführung in COM-Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) bei verwalteter Code in Anwendungsdomäne 1 ausgeführt wird verwalteten Code in Anwendungsdomäne 2 aufruft und der Code in Anwendungsdomäne 2 eine Ausnahme ausgelöst. Finden Sie unter [Programmieren mit Anwendungsdomänen](/dotnet/articles/framework/app-domains/index).  

3\) Wenn Code eine Funktion mit Reflexion aufgerufen, und die Funktion löst eine Ausnahme aus. Finden Sie unter [Reflektion](/dotnet/framework/reflection-and-codedom/reflection).  
  
In der Bedingung 2 und 3, wird die Ausnahme gelegentlich von verwaltetem Code in abgefangen `mscorlib` anstelle der common Language Runtime. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.  
  
**Debuggen auf Adressebene aktivieren** aktiviert erweiterte Funktionen für das Debuggen auf Adressebene (das **Disassembly** Fenster die **registriert** Fenster und Adresshaltepunkte).  
  
- **Disassembly anzeigen, wenn die Quelle nicht verfügbar ist** zeigt automatisch das **Disassembly** Fenster, wenn Sie versuchen, das Debuggen von Code für den der Quellcode nicht verfügbar ist.  
  
**Haltepunktfilter aktivieren** können Sie Filter an Haltepunkten festlegen, damit diese nur bestimmte Prozesse, Threads oder Computer gelten.  
 
**Verwenden Sie die neue Ausnahmen-Hilfe** ermöglicht es dem Ausnahmen-Hilfe (Visual Studio 2017), der Ausnahmen-Assistent ersetzt.
  
> [!NOTE]
> Bei verwaltetem Code ist diese Option hieß früher **des Ausnahmen-Assistenten aktivieren** . 
  
**Nur meinen Code aktivieren** der Debugger zeigt an, und in Einzelschritten aus Benutzercode ("Mein Code"), wird ignoriert, systemeigener und sonstiger Code, der optimiert ist oder ist und keine Debugsymbole.

- **Warnhinweis anzeigen, wenn kein Benutzercode beim Start (nur verwaltet)** beim Debuggen beginnt mit nur mein Code aktiviert diese Option warnt Sie, wenn kein Benutzercode ("Mein Code") vorhanden ist. 

**Aktivieren von .NET Framework-Quellcodes** kann der Debugger einen Einzelschritt in .NET Framework-Quelle. Durch Aktivieren dieser Option wird "Nur mein Code" automatisch deaktiviert. .NET Framework-Symbole werden an einen Cachespeicherort heruntergeladen. Sie können den Cachespeicherort im Ändern der **Optionen** Dialogfeld **Debuggen** Kategorie **Symbole** Seite.  
  
**Eigenschaften und Operatoren (nur verwaltet) überspringen** verhindert, dass den Debugger Eigenschaften und Operatoren in verwaltetem Code schrittweise.  
  
**Eigenschaftenauswertung und andere implizite Funktionsaufrufe** aktiviert die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in Variablenfenstern und **Schnellüberwachung** (Dialogfeld).  
  
- **Zeichenfolgenkonvertierungsfunktion für Objekte in Variablenfenstern (C#- und JavaScript nur) aufrufen** führt einen impliziten Zeichenkonvertierungsaufruf beim Auswerten von Objekten in Variablenfenstern. Das Ergebnis wird als eine Zeichenfolge anstelle der Typname angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann vom DebuggerDisplay-Attribut überschrieben werden (siehe [mithilfe des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Quellserverunterstützung aktivieren** weist den Visual Studio-Debugger an die Quelldateien aus den Quellservern abzurufen, die das SrcSrv implementieren (`srcsrv.dll`) Protokoll. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen zum SrcSrv-Setup finden Sie unter der [SrcSrv](https://msdn.microsoft.com/library/windows/hardware/ff558791(v=vs.85).aspx) Dokumentation. Darüber hinaus finden Sie unter [angeben von Symboldateien (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Da das Lesen von PDB-Dateien beliebigen Code in den Dateien ausführen kann, vergewissern Sie sich, dass Sie dem Server vertrauen können.  
  
- **Quelle diagnosemeldungen im Ausgabefenster Drucken** Wenn die quellserverunterstützung aktiviert ist, aktiviert diese Einstellung die diagnostische Anzeige.  
  
- **Quellserver für teilweise vertrauenswürdige Assemblys (nur verwaltet) zulassen** Wenn die quellserverunterstützung aktiviert ist, wird diese Einstellung überschreibt das Standardverhalten beim Nichtabrufen von Quellen für teilweise vertrauenswürdige Assemblys.  

**Aktivieren der Unterstützung von Quelllink** weist den Visual Studio-Debugger an Quelldateien für die PDB-Dateien herunterladen, die Quelle Linkinformationen enthalten. Weitere Informationen zu Quelllink finden Sie unter der [Link Quellspezifikation](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Because Source Link will download files using http or https, make sure you trust the .pdb file.  
  
**Bei Haltepunkten und aktueller Anweisung (nur C++) gesamte Zeile markieren** der Debugger einen Haltepunkt oder die aktuelle Anweisung hervorhebt, die die ganze Zeile hervorgehoben.  
  
**"Quelldateien" auf genau die ursprüngliche Version erfordern** weist den Debugger an, ob eine Quelldatei übereinstimmt, die Version des Quellcodes verwendet, um die ausführbare Datei erstellt, die Sie debuggen. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert, eine übereinstimmende Quelle zu suchen. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt. 
  
**Gesamten Text aus Ausgabefenster an das Direktfenster umleiten** sendet alle Debuggermeldungen, die normalerweise in der **Ausgabe** Fenster aus, um die **Direktfenster** Fenster stattdessen.  
  
**Unformatierte Struktur von Objekten in Variablenfenstern anzeigen** deaktiviert alle Anpassungen von objektstrukturansichten. Weitere Informationen zu ansichtsanpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten von .managed Objekte](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**JIT-Optimierung beim Laden von Modulen (nur verwaltet) unterdrücken** deaktiviert die JIT-Optimierung von verwaltetem Code aus, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt ist. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird. Weitere Informationen finden Sie unter [JIT-Optimierung und Debugging](../debugger/jit-optimization-and-debugging.md).

**Aktivieren Sie JavaScript-debugging für ASP.NET (Chrome und Internet Explorer)** ermöglicht es den Skriptdebugger für ASP.NET-Apps. Bei der ersten Verwendung in Chrome müssen Sie möglicherweise melden Sie sich der Browser bei der ersten Verwendung Aktivieren von Chrome-Erweiterungen, die Sie installiert haben. Deaktivieren Sie diese Option, um Legacyverhalten wiederherzustellen.    

**DLL‑Exporte laden** Dll-Exporttabellen lädt. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.  
  
Um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind, verwenden Sie `dumpbin /exports`. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
**Anzeigen parallelen Stapeln von unten nach oben im Diagramm** steuert die Richtung, in der Stapel, in angezeigt werden, der **parallele Stapel** Fenster.
  
**GPU Ausnahmen Speicherzugriff ignorieren, wenn die geschriebenen Daten nicht, den Wert geändert haben** ignoriert Racebedingungen, die erkannt wurden, während des Debuggens, wenn die Daten nicht geändert haben. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).  
  
**Verwalteten Kompatibilitätsmodus verwenden** ersetzt das standarddebugmodul durch eine Legacyversion, um diese Szenarien zu ermöglichen:  
  
- Sie verwenden eine andere .NET Framework-Sprache als C#, VB oder F#, die einen eigenen Expression Evaluator bereitstellt (dies schließt C++/CLI mit ein).  
  
- Sie möchten „Bearbeiten und Fortfahren“ für C++-Projekte beim Debuggen im gemischten Modus aktivieren.  
  
> [!NOTE]
> Auswählen des verwalteten Kompatibilitätsmodus deaktiviert den einige Funktionen, die nur im standardmäßigen Debugmodul implementiert werden. 

**Verwenden Sie die älteren c# und VB-ausdrucksauswertungen** der Debugger wird anstelle der Visual Studio 2015 Roslyn-basierten ausdrucksauswertungen die Visual Studio 2013 C#/VB-ausdrucksauswertungen verwenden.    
  
**Warnen, wenn benutzerdefinierte Debuggerschnellansichten gegen potenziell unsichere Prozesse (nur verwaltet) mit** Visual Studio warnt Sie bei Verwendung eine benutzerdefinierten Debuggerschnellansicht, die in der zu debuggenden Prozess Code ausgeführt wird, da er nicht sicher ausgeführt werden konnte Code.  
  
**Aktivieren der Windows Debug Heap reserviert wurde (nur systemeigen)** können Sie den Windows-Debugheap heapdiagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.  
  
**Aktivieren von UI-Debugtools für XAML** der Live Visual Tree und die Windows Live-Eigenschaften-Explorer werden angezeigt, wenn Sie eines unterstützten Projekttyps beginnen (F5) Debuggen. Weitere Informationen finden Sie unter [Überprüfen von XAML-Eigenschaften während des Debuggens](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Vorschau der ausgewählten Elemente in Live Visual Tree** der XAML-Element, dessen Kontext ausgewählt ist, wird ebenfalls ausgewählt, der **Live Visual Tree** Fenster.  
  
- **Anzeigen von Laufzeittools in Anwendung** zeigt die **Live Visual Tree** Befehle in einer Symbolleiste auf das Hauptfenster der Verwendung von XAML-Anwendung, die gedebuggt wird. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt. 

- **XAML-Code bearbeiten und Fortfahren aktivieren** bietet die Möglichkeit zum Verwenden von bearbeiten und Fortfahren-Funktion für die Verwendung von XAML-Code. 
  
**Aktivieren der Diagnosetools während des Debuggens** der **Diagnosetools** Fenster wird angezeigt, während des Debuggens.
  
**Perftip für verstrichene Zeit beim Debuggen anzeigen** das Codefenster zeigt die verstrichene Zeit von einem bestimmten Methodenaufruf während des Debuggens.  
  
**Bearbeiten und Fortfahren aktivieren** mithilfe von bearbeiten und Fortfahren Funktionalität während des Debuggens.  
  
- **Bearbeiten und Fortfahren aktivieren** mit bearbeiten und Fortfahren Funktionalität während des Debuggens von systemeigenem C++-Code. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Anwenden von Änderungen beim fortfahren (nur systemeigen)** Visual Studio automatisch kompiliert und wendet alle ausstehenden codeänderungen, die Sie vorgenommen haben, wenn den Prozess vom Zustand "Break" zu fortfahren. Wenn nicht ausgewählt ist, können Sie beim Übernehmen der Änderungen, die mithilfe des Elements "Codeänderungen übernehmen" im Menü "Debuggen" auswählen.  
  
- **Warnung bei veraltetem Code (nur systemeigen)** Warnungen über veralteten Code zu erhalten.    

**Anzeigen auf Schaltfläche im Editor während des Debuggens ausführen** Wenn diese Option aktiviert ist, die [ausführen, klicken Sie auf](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) Schaltfläche wird während des Debuggens angezeigt.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>In früheren Versionen von Visual Studio unterstützten Optionen

Wenn Sie eine ältere Version von Visual Studio verwenden, können einige zusätzlichen Optionen vorhanden sein.

**Aktivieren des Ausnahmen-Assistenten** für verwalteten Code aktiviert des Ausnahmen-Assistenten. In Visual Studio 2017 ersetzt den Ausnahmen-Hilfe des Ausnahmen-Assistenten.

**Aufrufliste für Ausnahmefehler entladen** bewirkt, dass die **Aufrufliste** Fenster aus, um die Aufrufliste an den Punkt zurücksetzt, bevor der Ausnahmefehler aufgetreten ist. 

**Warnhinweis anzeigen, wenn keine Symbole beim Starten (nur systemeigen)** wird ein Warnungsdialogfeld angezeigt, wenn Sie versuchen, ein Programm debuggen, für das der Debugger keine Symbolinformationen hat. 

**Warnhinweis anzeigen, wenn Skriptdebugging beim Start deaktiviert ist** wird ein Warnungsdialogfeld angezeigt, wenn der Debugger mit deaktiviertem Skriptdebuggen gestartet wird.

**Verwenden von systemeigenen Kompatibilitätsmodus** , wenn diese Option ausgewählt ist, verwendet der Debugger den systemeigenen Debugger von Visual Studio 2010 anstelle des neuen systemeigenen Debuggers.  
  
Beim Debuggen von .NET C++-Code sollten Sie diese Option verwenden, da die neue Debug-Engine das Auswerten von .NET C++-Ausdrücken nicht unterstützt. Durch das Aktivieren des nativen Kompatibilitätsmodus werden aber viele Funktionen deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. Beispielsweise legacymodul sind viele Schnellansichten für integrierte Typen wie `std::string` in Visual Studio 2015-Projekten.   Verwenden Sie Visual Studio 2013-Projekte für optimales debugging in diesen Fällen.
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
