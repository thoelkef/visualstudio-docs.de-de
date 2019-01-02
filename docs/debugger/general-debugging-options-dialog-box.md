---
title: Allgemein, Debuggen, Dialogfeld "Optionen" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/09/2018
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
ms.openlocfilehash: 4b5711b90e2b160f48c05835ae833bfbe7cd29fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730674"
---
# <a name="general-debugging-options"></a>Allgemeine Optionen für das Debuggen

Wählen Sie zum Festlegen von Optionen für Visual Studio-Debugger **Tools** > **Optionen**, und wählen Sie unter **Debuggen** aktivieren oder deaktivieren Sie die Kontrollkästchen neben den  **Allgemeine** Optionen. Sie können mit allen Standardeinstellungen wiederherstellen **Tools** > **Einstellungen importieren und exportieren** > **alle Einstellungen zurücksetzen**. Um eine Teilmenge der Einstellungen zurückzusetzen, speichern Sie die Einstellungen mit den **-Import- und Exportassistenten Einstellungen** vorzunehmende Änderungen, die Sie testen möchten, klicken Sie dann importieren Sie Ihre Einstellungen wurden gespeichert. anschließend.

Sie können festlegen, dass die folgenden **allgemeine** Optionen:

**Vor dem Löschen aller Haltepunkte Fragen**:  
Erfordert eine Bestätigung vor dem Abschluss der **alle Haltepunkte löschen** Befehl.

**Alle Prozesse anhalten, wenn ein Prozess anhält**:  
Hält im Falle einer Unterbrechung alle Prozesse gleichzeitig an, an die der Debugger angefügt ist.

**Ausnahmen unterbrechen oder verwaltete/systemeigene Übergänge überschreitenden**:  
Beim Debuggen im verwalteten oder gemischten Modus kann die Common Language Runtime die Ausnahmen auffangen, die die Grenzen zwischen Anwendungsdomänen oder Grenzen zwischen verwaltetem und systemeigenem Code überschreiten, wenn die folgenden Bedingungen erfüllt sind:

1. Bei nativem Code verwalteten Code mithilfe von COM-Interop und verwaltetem Code aufruft, wird eine Ausnahme ausgelöst. Finden Sie unter [Einführung in COM-Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Wenn verwalteter Code in Anwendungsdomäne 1 ausgeführt wird verwalteter Code in Anwendungsdomäne 2 aufgerufen und der Code in Anwendungsdomäne 2 eine Ausnahme ausgelöst. Finden Sie unter [Programmieren mit Anwendungsdomänen](/dotnet/articles/framework/app-domains/index).

3. Wenn Code eine Funktion mithilfe der Reflektion aufgerufen, und diese Funktion löst eine Ausnahme aus. Finden Sie unter [Reflektion](/dotnet/framework/reflection-and-codedom/reflection).

Unter Umständen 2 und 3 wird die Ausnahme gelegentlich von verwaltetem Code in abgefangen `mscorlib` und nicht von der common Language Runtime. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.

**Aktivieren Sie das Debuggen auf Adressebene**:  
Aktiviert erweiterte Funktionen für das Debuggen auf Adressebene (das **Disassembly** Fenster die **registriert** Fenster und Adresshaltepunkte).

- **Disassemblierung anzeigen, wenn die Quelle nicht verfügbar ist**:  
    Zeigt automatisch die **Disassembly** Fenster beim Debuggen von Code für die die Quelle nicht verfügbar ist.

**Haltepunktfilter aktivieren**:  
Mit dieser Option können Sie Filter an Haltepunkten festlegen, damit diese nur für bestimmte Prozesse, Threads oder Computer gelten.

**Verwenden Sie das neue Ausnahmehilfsprogramm**:  
Ermöglicht der Ausnahmen-Hilfe (Visual Studio 2017), die den Ausnahmen-Assistenten ersetzt.

> [!NOTE]
> Für verwalteten Code, der diese Option wurde bereits aufgerufen **Ausnahmen-Assistenten aktivieren** .

**Nur meinen Code aktivieren**:  
Der Debugger zeigt nur Benutzercode („Mein Code“) an und durchläuft ihn schrittweise, während systemeigener und sonstiger Code, der optimiert ist oder keine Debugsymbole aufweist, ignoriert wird.

- **Warnhinweis anzeigen, wenn kein Benutzercode beim Start (nur verwaltet)**:  
    Wenn beim Debuggen am Anfang "Nur mein Code" aktiviert ist, warnt diese Option Sie, wenn kein Benutzercode ("Eigener Code") vorhanden ist.

**Aktivieren von .NET Framework-Quellcodes**:  
Ermöglicht es dem Debugger, die .NET Framework-Quelle schrittweise auszuführen. Automatisch durch Aktivieren dieser Option wird nur mein Code deaktiviert. .NET Framework-Symbole werden an einen Cachespeicherort heruntergeladen. Ändern des cachespeicherorts mit der **Optionen** Dialogfeld **Debuggen** Kategorie **Symbole** Seite.

**Prozedurschritt für Eigenschaften und Operatoren überspringen (nur verwaltet)**:  
Verhindert, dass der Debugger Eigenschaften und Operatoren in verwaltetem Code schrittweise ausführt.

**Eigenschaftenauswertung und andere implizite Funktionsaufrufe**:  
Aktiviert die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in Variablenfenstern und **Schnellüberwachung** Dialogfeld.

- **Zeichenfolgenkonvertierungsfunktion für Objekte in Variablenfenstern aufrufen (C# nur und JavaScript)**:  
    Führt einen impliziten Zeichenkonvertierungsaufruf beim Auswerten von Objekten in Variablenfenstern aus. Das Ergebnis wird als eine Zeichenfolge anstatt in der Typname angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann vom DebuggerDisplay-Attribut überschrieben werden (siehe [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)).

**Quellserverunterstützung aktivieren**:  
Weist den Visual Studio-Debugger an, die Quelldateien aus den Quellservern abzurufen, die das SrcSrv-Protokoll (`srcsrv.dll`) implementieren. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen zum SrcSrv-Setup finden Sie unter den [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) Dokumentation. Darüber hinaus finden Sie unter [angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Da beim Lesen der *PDB* Dateien beliebigen Code auszuführen, in den Dateien, stellen Sie sicher, dass Sie auf den Server vertrauen können.

- **Source Server-diagnosemeldungen im Ausgabefenster Drucken**:  
    Wenn die Quellserverunterstützung aktiviert ist, aktiviert diese Einstellung die diagnostische Anzeige.

- **Quellserver für teilweise vertrauenswürdige Assemblys (nur verwaltet) zulassen**:  
    Wenn die Quellserverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten beim Nichtabrufen von Quellen für teilweise vertrauenswürdige Assemblys.

- **Immer nicht vertrauenswürdigen Quellserverbefehle ohne Aufforderung ausführen**:  
    Wenn die quellserverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten von eingabeaufforderungen festzulegen, wenn es sich bei einen nicht vertrauenswürdigen Befehl ausführen.

**Quelllinkunterstützung aktivieren**:  
    Weist den Visual Studio-Debugger zum Herunterladen der Quelldateien für *PDB* Dateien, die Informationen der Link "Quelle" enthalten. Weitere Informationen zu den Link "Quelle", finden Sie unter den [quellenspezifikation-Verknüpfung](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
>  Da der Link "Quelle" werden Dateien, die über http oder Https heruntergeladen haben, stellen Sie sicher, dass Sie vertrauen den *PDB* Datei.

- **Reduzierung auf Git Credential Manager-Authentifizierung für alle Anforderungen für Quelllinks**:  
    Wenn Unterstützung für Quelllink aktiviert ist und eine Anforderung der Link "Quelle" schlägt die Authentifizierung fehl, ruft Visual Studio klicken Sie dann Git Credential Manager.

**Bei Haltepunkten und aktueller Anweisung (nur C++) die gesamte Zeile markieren**:  
Wenn der Debugger einen Haltepunkt oder die aktuelle Anweisung hervorhebt, wird die ganze Zeile hervorgehoben.

**Quelldateien müssen genau mit übereinstimmen, die ursprüngliche Version**:  
Fordert den Debugger auf, zu prüfen, ob die Quelldatei mit der Version des Quellcodes übereinstimmt, mit dem die ausführbare Datei erstellt wurde, die Sie debuggen. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert, eine übereinstimmende Quelle zu suchen. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt.

**Gesamten Text aus Ausgabefenster an das Direktfenster umleiten**:  
Sendet alle Debuggermeldungen, die normalerweise in der **Ausgabe** Fenster aus, um die **direkt** Fenster stattdessen.

**Unformatierte Struktur von Objekten in Variablenfenstern anzeigen**:  
Deaktiviert alle Anpassungen von Objektstrukturansichten. Weitere Informationen zu ansichtsanpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-dot-managed-objects.md).

**JIT-Optimierung beim Laden von Modulen (nur verwaltet) unterdrücken**:  
Deaktiviert die JIT-Optimierung von verwaltetem Code, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt ist. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird. Weitere Informationen finden Sie unter [JIT-Optimierung und-Debuggen](../debugger/jit-optimization-and-debugging.md).

**Aktivieren Sie JavaScript-debugging für ASP.NET (Chrome, Microsoft Edge und IE)**:  
Ermöglicht es den Skriptdebugger für ASP.NET-Apps. Bei der ersten Verwendung in Chrome müssen Sie sich in den Browser Chrome-Erweiterungen zu aktivieren, die Sie installiert haben. Deaktivieren Sie diese Option, um zum alten Verhalten zurückzukehren.

**Aktivieren Sie Microsoft Edge-Entwicklertools für UWP-JavaScript-Apps (experimentell)**:  
Ermöglicht die Entwicklertools für UWP-JavaScript-apps in Microsoft Edge.

**Aktivieren von legacy-Chrome-JavaScript-Debugger für ASP.NET**:  
Kann den legacy-Chrome-JavaScript-Skriptdebugger für ASP.NET-Apps. Bei der ersten Verwendung in Chrome müssen Sie sich in den Browser Chrome-Erweiterungen zu aktivieren, die Sie installiert haben.

**Verwenden Sie die experimentelle Möglichkeit zum Starten, wenn Visual Studio als Administrator ausführen Chrome-JavaScript-debugging**:  
Teilt Visual Studio, um eine neue Methode zum Chrome während der JavaScript-debugging zu starten. versuchen Sie es.

**(Nur systemeigen) der Dll-Exporte laden**:  
Lädt DLL‑Exporttabellen. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.

Verwenden Sie `dumpbin /exports`, um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](/cpp/build/reference/dash-exports).

**Show parallelen Stapeln von unten nach oben im Diagramm**:  
Steuert die Richtung, in der Stapel, in angezeigt werden, der **parallele Stapel** Fenster.

**GPU Ausnahmen Speicherzugriff ignorieren, wenn die geschriebenen Daten nicht geändert haben**:  
Ignoriert Racebedingungen, die erkannt wurden, während des Debuggens, wenn die Daten nicht geändert haben. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).

**Verwalteten Kompatibilitätsmodus verwenden**:  
Ersetzt die Standarddebug-Engine durch eine Legacyversion, um die folgenden Szenarien zu ermöglichen:

- Verwenden Sie .NET Framework-Sprache außer C#, Visual Basic oder F# , einen eigenen Expression Evaluator bereitstellt (Dies schließt C++ / CLI).

- Sie möchten bearbeiten und Fortfahren für C++-Projekte beim Debuggen im gemischten Modus aktivieren.

> [!NOTE]
> Auswählen des verwalteten Kompatibilitätsmodus deaktiviert Modus einige Features, die nur im standardmäßigen Debugmodul implementiert werden.

**Verwenden Sie die Vorgängerversion C# und VB-ausdrucksauswertungen**:  
Der Debugger verwendet Visual Studio 2013 C# oder VB-ausdrucksauswertungen anstelle der Visual Studio 2015 Roslyn-basierten ausdrucksauswertungen.

**Warnen, wenn benutzerdefinierte Debugger für die Anzeige potenziell unsicherer Prozesse (nur verwaltet) mit**:  
Visual Studio warnt Sie bei Verwendung eine benutzerdefinierten Debuggerschnellansicht, die im gedebuggten Prozess Code ausgeführt wird, da er unsicheren Code ausgeführt werden konnte.

**Heapzuweisung von Windows Debug (nur systemeigen)**:  
Aktiviert den Debugheap von Windows, um die Heapdiagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.

**UI-Debuggingtools für XAML aktivieren**:  
Live Visual Tree und die Live-Eigenschaften-Explorer-Fenster werden angezeigt, wenn Sie das Debuggen starten (**F5**) eines unterstützten Projekttyps. Weitere Informationen finden Sie unter [Überprüfen von XAML-Eigenschaften während des Debuggens](../debugger/inspect-xaml-properties-while-debugging.md).

- **Vorschau der ausgewählten Elemente in visuelle Echtzeitstruktur**:  
    Das XAML-Element, dessen Kontext ausgewählt ist, ebenfalls ausgewählt ist, der **Live Visual Tree** Fenster.

- **Laufzeittools in Anwendung**:  
    Zeigt die **Live Visual Tree** Befehle in einer Symbolleiste des Hauptfensters der XAML-Anwendung, die gedebuggt wird. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt.

- **Aktivieren Sie die XAML bearbeiten und Fortfahren**:  
    Ermöglicht Ihnen, verwenden die Bearbeitung und Fortsetzen von XAML-Code-Funktion.

**Aktivieren der Diagnosetools während des Debuggens**:  
Die **Diagnosetools** Fenster wird angezeigt, während des Debuggens.

**PerfTip für verstrichene Zeit beim Debuggen anzeigen**:  
Das Codefenster zeigt an, wie viel Zeit bei einem bestimmten Methodenaufruf während des Debuggens verstrichen ist.

**Bearbeiten und Fortfahren aktivieren**:  
Ermöglicht die bearbeiten und Fortfahren-Funktionalität während des Debuggens.

- **Aktivieren Sie systemeigene bearbeiten und Fortfahren**:  
    Sie können die Funktion „Bearbeiten und Fortfahren“ während des Debuggens von systemeigenem C++-Code verwenden. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Anwenden von Änderungen beim fortfahren (nur systemeigen)**:  
    Beim Fortsetzen eines unterbrochenen Prozesses kompiliert Visual Studio automatisch alle ausstehenden Codeänderungen und wendet sie an. Wenn nicht ausgewählt ist, können Sie zum Anwenden von Änderungen, die mit der **Codeänderungen übernehmen** Element der **Debuggen** Menü.

- **Warnung bei veraltetem Code (nur systemeigen)**:  
    Ruft Warnungen über veralteten Code ab.

**Ausführung bis Klick anzeigen-Schaltfläche im Editor während des Debuggens**:  
Wenn diese Option ausgewählt ist, die [Ausführung bis Klick](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) Schaltfläche wird während des Debuggens angezeigt.

**Schließen Sie die Konsole automatisch nach Beenden des Debuggings**:  
Teilt Visual Studio, um die Konsole schließen, am Ende einer Debugsitzung an.

## <a name="options-available-in-older-versions-of-visual-studio"></a>In früheren Versionen von Visual Studio verfügbaren Optionen

Wenn Sie eine ältere Version von Visual Studio verwenden, können einige zusätzlichen Optionen vorhanden sein.

**Ausnahmen-Assistenten aktivieren**:  
Für verwalteten Code können Ausnahmen-Assistenten. In Visual Studio 2017 ersetzt der Ausnahmen-Hilfe des Ausnahmen-Assistenten.

**Aufrufliste für Ausnahmefehler entladen**:  
Bewirkt, dass die **Aufrufliste** Fenster aus, um ein Rollback die Aufrufliste zu dem Punkt, bevor der Ausnahmefehler aufgetreten ist.

**Warnhinweis anzeigen, wenn keine Symbole beim Starten (nur systemeigen)**:  
Zeigt eine Warnmeldung angezeigt, wenn Sie ein Programm debuggen, für die der Debugger keine Symbolinformationen hat.

**Warnhinweis anzeigen, wenn Skriptdebugging beim Start deaktiviert ist**:  
Zeigt ein Warnungsdialogfeld an, wenn der Debugger mit deaktiviertem Skriptdebuggen gestartet wird.

**Systemeigenen Kompatibilitätsmodus verwenden**:  
Wenn diese Option ausgewählt ist, wird der native Debugger von Visual Studio 2010 anstelle des neuen nativen Debuggers verwendet.

- Verwenden Sie diese Option beim .NET C++-Code Debuggen, da die neuen Debugmodul das Auswerten von .NET C++-Ausdrücken nicht unterstützt. Durch das Aktivieren des nativen Kompatibilitätsmodus werden aber viele Funktionen deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. Z. B. die legacy-Engine verfügt nicht über viele Schnellansichten für integrierte Typen wie `std::string` in Visual Studio 2015-Projekten.   Verwenden Sie Visual Studio 2013-Projekte für optimales debugging in diesen Fällen an.

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.md)
- [Debugger – Featuretour](../debugger/debugger-feature-tour.md)