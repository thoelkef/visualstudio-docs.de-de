---
title: Allgemein, Debuggen, Dialogfeld "Optionen" | Microsoft Docs
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
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
helpviewer_keywords: Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: "46"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c7f6983c2be5604867f729ed006eadb5257c3a43
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="general-debugging-options-dialog-box"></a>Allgemein, Debuggen, Dialogfeld "Optionen"
Die **Extras > Optionen > Debugging > Allgemein** Seite können Sie die folgenden Optionen festlegen:  
  
**Vor dem Löschen aller Haltepunkte Fragen**  
Erfordert eine Bestätigung vor dem Abschluss der **alle Breakpoints löschen** Befehl.  
  
**Anhalten Sie alle Prozesse, wenn ein Prozess anhält**  
Hält im Falle einer Unterbrechung alle Prozesse gleichzeitig an, an die der Debugger angefügt ist.  
  
**Überschreitenden Ausnahmen bei Anwendungsdomänengrenzen oder verwaltete/systemeigene unterbrechen**  
Beim Debuggen im verwalteten oder gemischten Modus kann die Common Language Runtime die Ausnahmen auffangen, die die Grenzen zwischen Anwendungsdomänen oder Grenzen zwischen verwaltetem und systemeigenem Code überschreiten, wenn die folgenden Bedingungen erfüllt sind:  
  
1\) bei systemeigenem Code verwalteter Code mit COM-Interop aufgerufen und der verwaltete Code löst eine Ausnahme aus. Finden Sie unter [Einführung in COM-Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) bei verwalteter Code in Anwendungsdomäne 1 ausgeführt wird verwalteten Code in Anwendungsdomäne 2 aufruft und der Code in Anwendungsdomäne 2 eine Ausnahme ausgelöst. Finden Sie unter [Programmieren mit Anwendungsdomänen](/dotnet/articles/framework/app-domains/index).  

3\) Wenn Code eine Funktion mit Reflexion aufgerufen, und die Funktion löst eine Ausnahme aus. Finden Sie unter [Reflektion](/dotnet/framework/reflection-and-codedom/reflection).  
  
In der Bedingung 2 und 3, wird die Ausnahme gelegentlich von verwaltetem Code in abgefangen `mscorlib` anstelle der common Language Runtime. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.  
  
**Debuggen auf Adressebene aktivieren**  
 Aktiviert erweiterte Funktionen für das Debuggen auf Adressebene (das **Disassembly** Fenster die **registriert** Fenster und Adresshaltepunkte).  
  
- **Zeigen Sie Disassembly an, wenn die Quelle nicht verfügbar ist.**  
    Zeigt automatisch das **Disassembly** Fenster, wenn Sie versuchen, das Debuggen von Code für den der Quellcode nicht verfügbar ist.  
  
**Haltepunktfilter aktivieren**  
Mit dieser Option können Sie Filter an Haltepunkten festlegen, damit diese nur für bestimmte Prozesse, Threads oder Computer gelten.  
 
**Verwenden Sie die neue Ausnahmen-Hilfe**  
Ermöglicht es dem Ausnahmen-Hilfe (Visual Studio 2017), der Ausnahmen-Assistent ersetzt.
  
> [!NOTE]
> Bei verwaltetem Code ist diese Option hieß früher **des Ausnahmen-Assistenten aktivieren** . 
  
**Nur meinen Code aktivieren**  
Der Debugger zeigt nur Benutzercode („Mein Code“) an und durchläuft ihn schrittweise, während systemeigener und sonstiger Code, der optimiert ist oder keine Debugsymbole aufweist, ignoriert wird.

- **Warnhinweis anzeigen Sie, wenn kein Benutzercode beim Start (nur verwaltet)**  
    Wenn beim Debuggen am Anfang "Nur mein Code" aktiviert ist, warnt diese Option Sie, wenn kein Benutzercode ("Eigener Code") vorhanden ist. 

**Aktivieren von .NET Framework-Quellcodes**  
Ermöglicht es dem Debugger, die .NET Framework-Quelle schrittweise auszuführen. Durch Aktivieren dieser Option wird "Nur mein Code" automatisch deaktiviert. .NET Framework-Symbole werden an einen Cachespeicherort heruntergeladen. Sie können den Cachespeicherort im Ändern der **Optionen** Dialogfeld **Debuggen** Kategorie **Symbole** Seite.  
  
**Prozedurschritt für Eigenschaften und Operatoren (nur verwaltet)**  
Verhindert, dass der Debugger Eigenschaften und Operatoren in verwaltetem Code schrittweise ausführt.  
  
**Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**  
Aktiviert die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in Variablenfenstern und **Schnellüberwachung** (Dialogfeld).  
  
- **Zeichenfolgenkonvertierungsfunktion für Objekte in Variablenfenstern (C#- und JavaScript nur) aufrufen.**  
    Führt einen impliziten Zeichenkonvertierungsaufruf beim Auswerten von Objekten in Variablenfenstern aus. Deshalb wird dieses Ergebnis nicht als Typname, sondern als Zeichenfolge angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann vom DebuggerDisplay-Attribut überschrieben werden (siehe [mithilfe des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Quellserverunterstützung aktivieren**  
Weist den Visual Studio-Debugger an, die Quelldateien aus den Quellservern abzurufen, die das SrcSrv-Protokoll (`srcsrv.dll`) implementieren. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen zum SrcSrv-Setup finden Sie unter der [SrcSrv](https://msdn.microsoft.com/library/windows/hardware/ff558791(v=vs.85).aspx) Dokumentation. Darüber hinaus finden Sie unter [angeben von Symboldateien (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Da das Lesen von PDB-Dateien beliebigen Code in den Dateien ausführen kann, vergewissern Sie sich, dass Sie dem Server vertrauen können.  
  
- **Drucken Sie Quelle diagnosemeldungen im Ausgabefenster**  
    Wenn die Quellserverunterstützung aktiviert ist, aktiviert diese Einstellung die diagnostische Anzeige.  
  
- **Quellserver für teilweise vertrauenswürdige Assemblys (nur verwaltet) zulassen**  
    Wenn die Quellserverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten beim Nichtabrufen von Quellen für teilweise vertrauenswürdige Assemblys.  

- **Unterstützung für Datenquellen Link aktivieren**  
    Weist den Visual Studio-Debugger zum Herunterladen von Quelldateien nach PDB-Dateien, die Quelle Linkinformationen enthalten. Weitere Informationen zu Quelllink finden Sie unter der [Link Quellspezifikation](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Da die Quelllink Dateien, die über http oder Https heruntergeladen wird, stellen Sie sicher, dass Sie die PDB-Datei als vertrauenswürdig einstufen.  
  
**Markieren Sie bei Haltepunkten und aktueller Anweisung (nur C++) gesamte Zeile**  
Wenn der Debugger einen Haltepunkt oder die aktuelle Anweisung hervorhebt, wird die ganze Zeile hervorgehoben.  
  
**Quelldateien Sie müssen exakt der Originalversion übereinstimmen**  
Fordert den Debugger auf, zu prüfen, ob die Quelldatei mit der Version des Quellcodes übereinstimmt, mit dem die ausführbare Datei erstellt wurde, die Sie debuggen. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert, eine übereinstimmende Quelle zu suchen. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt. 
  
**Umleiten Sie gesamten Text aus Ausgabefenster an das Direktfenster**  
Sendet alle Debuggermeldungen, die normalerweise in der **Ausgabe** Fenster aus, um die **Direktfenster** Fenster stattdessen.  
  
**Unformatierte Struktur von Objekten in Variablenfenstern anzeigen**  
Deaktiviert alle Anpassungen von Objektstrukturansichten. Weitere Informationen zu ansichtsanpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten von .managed Objekte](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Unterdrücken der JIT-Optimierung beim Laden von Modulen (nur verwaltet)**  
Deaktiviert die JIT-Optimierung von verwaltetem Code, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt ist. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird.

**Aktivieren Sie JavaScript-debugging für ASP.NET (Chrome und Internet Explorer)** ermöglicht es den Skriptdebugger für ASP.NET-Apps. Bei der ersten Verwendung in Chrome müssen Sie möglicherweise melden Sie sich der Browser bei der ersten Verwendung Aktivieren von Chrome-Erweiterungen, die Sie installiert haben. Deaktivieren Sie diese Option, um Legacyverhalten wiederherzustellen.    

**DLL‑Exporte laden**  
Lädt DLL‑Exporttabellen. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.  
  
Um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind, verwenden Sie `dumpbin /exports`. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
**Parallele Stapel Diagramm von unten nach oben anzeigen**  
Steuert die Richtung, in der Stapel, in angezeigt werden, der **parallele Stapel** Fenster.  
  
**Ignorieren Sie GPU Ausnahmen Speicherzugriff, wenn die geschriebenen Daten der Wert geändert wurde**  
Ignoriert Racebedingungen, die erkannt wurden, während des Debuggens, wenn die Daten nicht geändert haben. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).  
  
**Verwalteten Kompatibilitätsmodus verwenden**  
Ersetzt das Standarddebugmodul durch eine Legacyversion, um die folgenden Szenarien zu ermöglichen:  
  
- Sie verwenden eine andere .NET Framework-Sprache als C#, VB oder F#, die einen eigenen Expression Evaluator bereitstellt (dies schließt C++/CLI mit ein).  
  
- Sie möchten „Bearbeiten und Fortfahren“ für C++-Projekte beim Debuggen im gemischten Modus aktivieren.  
  
Beachten Sie, dass durch Auswählen des verwalteten Kompatibilitätsmodus einige Funktionen deaktiviert werden, die nur im standardmäßigen Debugmodul implementiert werden. 

**Verwenden Sie die älteren c# und VB-ausdrucksauswertungen**  
Der Debugger verwendet anstelle der Visual Studio 2015 Roslyn-basierten Ausdrucksauswertungen die Visual Studio 2013 C#/VB-Ausdrucksauswertungen.    
  
**Warnhinweis anzeigen Sie, bei Verwendung von benutzerdefinierten Debuggerschnellansichten gegen potenziell unsichere Prozesse (nur verwaltet)**  
Visual Studio warnt Sie bei Verwendung einer benutzerdefinierten Debuggerschnellansicht, die im zu debuggenden Prozess Code ausführt, da es sich um unsicheren Code handeln könnte.  
  
**Aktivieren der Windows Debug Heap reserviert wurde (nur systemeigen)**  
Aktiviert den Debugheap von Windows, um die Heapdiagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.  
  
**Aktivieren von UI-Debugtools für XAML**  
Die Fenster „Visuelle Echtzeitstruktur“ und „Echtzeit-Eigenschaften-Explorer“ werden angezeigt, wenn Sie mit dem Debuggen eines unterstützten Projekttyps beginnen (F5). Weitere Informationen finden Sie unter [Überprüfen von XAML-Eigenschaften während des Debuggens](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Voransicht für ausgewählte Elemente in Live Visual Tree anzeigen**  
    Das XAML-Element, dessen Kontext ausgewählt ist, wird auch ausgewählt der **Live Visual Tree** Fenster.  
  
- **Common Language Runtime-Tools in der Anwendung anzeigen**  
    Zeigt die **Live Visual Tree** Befehle in einer Symbolleiste auf das Hauptfenster der Verwendung von XAML-Anwendung, die gedebuggt wird. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt. 

- **XAML-Code bearbeiten und Fortfahren aktivieren** bietet die Möglichkeit zum Verwenden von bearbeiten und Fortfahren-Funktion für die Verwendung von XAML-Code. 
  
**Aktivieren der Diagnosetools während des Debuggens**  
Die **Diagnosetools** Fenster wird angezeigt, während des Debuggens.
  
**Perftip für verstrichene Zeit beim Debuggen anzeigen**  
Das Codefenster zeigt an, wie viel Zeit bei einem bestimmten Methodenaufruf während des Debuggens verstrichen ist.  
  
**Bearbeiten und Fortfahren aktivieren**  
Sie können die Funktion „Bearbeiten und Fortfahren“ während des Debuggens verwenden.  
  
- **Aktivieren Sie systemeigene bearbeiten und fortfahren**  
    Sie können die Funktion „Bearbeiten und Fortfahren“ während des Debuggens von systemeigenem C++-Code verwenden. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Anwenden von Änderungen beim fortfahren (nur systemeigen)**  
    Beim Fortsetzen eines unterbrochenen Prozesses kompiliert Visual Studio automatisch alle ausstehenden Codeänderungen und wendet sie an. Wenn nicht ausgewählt ist, können Sie beim Übernehmen der Änderungen, die mithilfe des Elements "Codeänderungen übernehmen" im Menü "Debuggen" auswählen.  
  
- **Warnung bei veraltetem Code (nur systemeigen)**  
    Ruft Warnungen über veralteten Code ab.    

**Anzeigen auf Schaltfläche im Editor während des Debuggens ausführen** Wenn diese Option aktiviert ist, die [ausführen, klicken Sie auf](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) Schaltfläche wird während des Debuggens angezeigt.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>In früheren Versionen von Visual Studio unterstützten Optionen

Wenn Sie eine ältere Version von Visual Studio verwenden, können einige zusätzlichen Optionen vorhanden sein.

**Aktivieren des Ausnahmen-Assistenten**  
Für verwalteten Code aktiviert des Ausnahmen-Assistenten. In Visual Studio 2017 ersetzt den Ausnahmen-Hilfe des Ausnahmen-Assistenten.

**Aufrufliste für Ausnahmefehler entladen**  
Bewirkt, dass die **Aufrufliste** Fenster aus, um die Aufrufliste an den Punkt zurücksetzt, bevor der Ausnahmefehler aufgetreten ist. 

**Warnhinweis anzeigen Sie, wenn keine Symbole beim Starten (nur systemeigen)**  
Zeigt eine Warnungsdialogfeld an, wenn Sie ein Programm debuggen, für das der Debugger keine Symbolinformationen hat. 

**Warnhinweis anzeigen Sie, wenn Skriptdebugging beim Start deaktiviert ist**  
Zeigt ein Warnungsdialogfeld an, wenn der Debugger mit deaktiviertem Skriptdebuggen gestartet wird.

**Systemeigenen Kompatibilitätsmodus verwenden**  
Wenn diese Option ausgewählt ist, wird der native Debugger von Visual Studio 2010 anstelle des neuen nativen Debuggers verwendet.  
  
Beim Debuggen von .NET C++-Code sollten Sie diese Option verwenden, da das neue Debugmodul das Auswerten von .NET C++-Ausdrücken nicht unterstützt. Durch das Aktivieren des nativen Kompatibilitätsmodus werden aber viele Funktionen deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. Beispielsweise legacymodul sind viele Schnellansichten für integrierte Typen wie `std::string` in Visual Studio 2015-Projekten.   Verwenden Sie für ein optimales Debugging in diesen Fällen Visual Studio 2013-Projekte.
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
