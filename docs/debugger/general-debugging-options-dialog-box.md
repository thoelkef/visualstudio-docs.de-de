---
title: Allgemein, Debuggen, Dialog Feld "Optionen" | Microsoft-Dokumentation
ms.date: 11/09/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03634b5a2bd1417e75f843fd9026712313f1923d
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987630"
---
# <a name="general-debugging-options"></a>Allgemeine Debugoptionen

Um die Visual Studio-Debuggeroptionen **festzulegen, wählen Sie** > Extras**Optionen**aus, und wählen Sie unter **Debuggen** die Kontrollkästchen neben den **allgemeinen** Optionen aus. Sie können alle Standardeinstellungen mit den **Tools** > **Import-und Export Einstellungen** > alle**Einstellungen zurücksetzen**wiederherstellen. Wenn Sie eine Teilmenge der Einstellungen zurücksetzen möchten, speichern Sie Ihre Einstellungen mit dem **Assistenten zum Importieren und Exportieren von Einstellungen** , bevor Sie die Änderungen vornehmen, die Sie testen möchten, und importieren Sie anschließend die gespeicherten Einstellungen.

Sie können die folgenden **allgemeinen** Optionen festlegen:

**Vor Löschen aller Haltepunkte fragen**: Erfordert zum Ausführen des Befehls **Alle Haltepunkte löschen** die Bestätigung.

**Alle Prozesse anhalten, wenn ein Prozess anhält**: Hält im Falle einer Unterbrechung alle Prozesse gleichzeitig an, an die der Debugger angefügt ist.

**Bei Anwendungsdomänengrenzen oder verwaltete/native Übergänge überschreitenden Ausnahmen unterbrechen**: Beim Debuggen im verwalteten oder gemischten Modus kann die Common Language Runtime die Ausnahmen auffangen, die die Grenzen zwischen Anwendungsdomänen oder Grenzen zwischen verwaltetem und systemeigenem Code überschreiten, wenn die folgenden Bedingungen erfüllt sind:

1. Wenn in nativem Code verwalteter Code mit COM-Interop aufgerufen wird und im verwalteten Code eine Ausnahme ausgelöst wird. Weitere Informationen finden [Sie unter Einführung in COM-Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Wenn verwalteter Code, der in der Anwendungsdomäne 1 ausgeführt wird, verwalteten Code in der Anwendungsdomäne 2 aufruft und der Code in Anwendungsdomäne 2 eine Ausnahme auslöst. Siehe [Programmieren mit Anwendungsdomänen](/dotnet/articles/framework/app-domains/index).

3. Wenn Code eine Funktion mit Reflektion aufruft und diese Funktion eine Ausnahme auslöst. Siehe [Reflektion](/dotnet/framework/reflection-and-codedom/reflection).

In den Bedingungen 2 und 3 wird die Ausnahme manchmal von verwaltetem Code in `mscorlib` und nicht vom Common Language Runtime abgefangen. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.

**Debugging auf Adressebene aktivieren**: Aktiviert erweiterte Funktionen für das Debuggen auf Adressebene (das Fenster **Disassembly**, das Fenster **Register** und Adresshaltepunkte).

- **Disassembly anzeigen, wenn die Quelle nicht verfügbar ist**:   Das Fenster **Disassembly** wird automatisch angezeigt, wenn Sie Code Debuggen, für den die Quelle nicht verfügbar ist.

**Haltepunktfilter aktivieren**: Mit dieser Option können Sie Filter an Haltepunkten festlegen, damit diese nur für bestimmte Prozesse, Threads oder Computer gelten.

**Die neue Ausnahmen-Hilfe verwenden**: Aktiviert die Ausnahme-Hilfe, die den Ausnahmen-Assistenten ersetzt. (Ausnahmen-Hilfsprogramm wird ab Visual Studio 2017 unterstützt.)

> [!NOTE]
> Bei verwaltetem Code wurde diese Option zuvor als **enable the Exception Assistant** bezeichnet.

**Nur eigenen Code aktivieren**: Der Debugger zeigt nur Benutzercode („Mein Code“) an und durchläuft ihn schrittweise, während systemeigener und sonstiger Code, der optimiert ist oder keine Debugsymbole aufweist, ignoriert wird.

- **Warnen, wenn beim Starten kein Benutzercode ausgeführt wird (nur verwaltet)** :   Wenn beim Debuggen am Anfang "Nur mein Code" aktiviert ist, warnt diese Option Sie, wenn kein Benutzercode ("Eigener Code") vorhanden ist.

**Durchlaufen des .NET Framework-Quellcodes aktivieren**: Ermöglicht es dem Debugger, die .NET Framework-Quelle schrittweise auszuführen. Wenn Sie diese Option aktivieren, wird nur eigenen Code automatisch deaktiviert. .NET Framework Symbole werden an einen Cache Speicherort heruntergeladen. Ändern Sie den Cache Speicherort, indem Sie das Dialogfeld **Optionen** , **debugkategorie** , **Symbol** Seite auswählen.

**Eigenschaften und Operatoren überspringen (nur verwaltet)** : Verhindert, dass der Debugger Eigenschaften und Operatoren in verwaltetem Code schrittweise ausführt.

**Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**: Aktiviert die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in Variablenfenstern und im Dialogfeld **Schnellüberwachung**.

- **Zeichenfolgenkonvertierungsfunktion für Objekte in Variablenfenstern aufrufen (nur C# und JavaScript)** : Führt einen impliziten Zeichenkonvertierungsaufruf beim Auswerten von Objekten in Variablenfenstern aus. Das Ergebnis wird als Zeichenfolge anstelle des Typnamens angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann durch das Attribut "tbuggerdisplay" überschrieben werden (siehe [Verwenden des Attributs](../debugger/using-the-debuggerdisplay-attribute.md)"Debug-Display").

**Quellserverunterstützung aktivieren**: Weist den Visual Studio-Debugger an, die Quelldateien aus den Quellservern abzurufen, die das SrcSrv-Protokoll (`srcsrv.dll`) implementieren. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen zum SrcSrv-Setup finden Sie in der [SRCSRV](/windows-hardware/drivers/debugger/srcsrv) -Dokumentation. Weitere Informationen finden Sie unter [Angeben von Symbol-(PDB-) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Da das Lesen von *PDB*-Dateien beliebigen Code in den Dateien ausführen kann, vergewissern Sie sich, dass Sie dem Server vertrauen können.

- **Diagnosemeldungen für Quellserver im Ausgabefenster drucken**:   Wenn die Quellserverunterstützung aktiviert ist, aktiviert diese Einstellung die diagnostische Anzeige.

- **Quellserver für teilweise vertrauenswürdige Assemblys (nur verwaltet) zulassen**:   Wenn die Quellserverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten beim Nichtabrufen von Quellen für teilweise vertrauenswürdige Assemblys.

- **Alle nicht vertrauenswürdigen Quellserverbefehle ohne Aufforderung ausführen**:   Wenn die Quell Serverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten der Eingabeaufforderung, wenn ein nicht vertrauenswürdiger Befehl ausgeführt wird.

**Quelllinkunterstützung aktivieren**: Weist den Visual Studio-Debugger an, Quelldateien für *PDB* -Dateien herunterzuladen, die Informationen zur Quell Verknüpfung enthalten. Weitere Informationen zum quelllink finden Sie in der [Spezifikation für den Quell Link](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
> Da der quelllink Dateien mithilfe von http oder HTTPS herunterlädt, sollten Sie sicherstellen, dass Sie der *PDB* -Datei vertrauen.

- **Für alle Quellenlinkanforderungen Fallback auf die Authentifizierung über die Git-Anmeldeinformationsverwaltung durchführen**:   Wenn die Unterstützung für Quell Verknüpfungen aktiviert ist und eine Quell Verknüpfungs Anforderung die Authentifizierung nicht erfolgreich durchführt, ruft Visual Studio die git Credential Manager auf.

**Gesamte Zeile für Breakpoints und Current-Anweisung markierenC++ (nur)** : Wenn der Debugger einen Haltepunkt oder die aktuelle Anweisung hervorhebt, wird die ganze Zeile hervorgehoben.

**Quelldateien müssen exakt mit der Originalversion übereinstimmen**: Fordert den Debugger auf, zu prüfen, ob die Quelldatei mit der Version des Quellcodes übereinstimmt, mit dem die ausführbare Datei erstellt wurde, die Sie debuggen. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert, eine passende Quelle zu suchen. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt.

**Gesamten Text aus Ausgabefenster an das Direktfenster umleiten**: Sendet alle Debuggermeldungen, die normalerweise im **Ausgabefenster** angezeigt werden, an das **Direktfenster**.

**Unformatierte Struktur von Objekten in Variablenfenstern anzeigen**: Deaktiviert alle Anpassungen von Objektstrukturansichten. Weitere Informationen zu Ansichts Anpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-dot-managed-objects.md).

**JIT-Optimierung beim Laden von Modulen unterdrücken (nur verwaltet)** : Deaktiviert die JIT-Optimierung von verwaltetem Code, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt ist. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird. Weitere Informationen finden Sie unter [JIT-Optimierung und-Debuggen](../debugger/jit-optimization-and-debugging.md).

**Aktivieren Sie JavaScript-debugging für ASP.NET (Chrome, Microsoft Edge und IE)** : Aktiviert den Skript Debugger für ASP.net-apps. Bei der ersten Verwendung in Chrome müssen Sie sich möglicherweise beim Browser anmelden, um Chrome-Erweiterungen zu aktivieren, die Sie installiert haben. Deaktivieren Sie diese Option, um das Legacy Verhalten wiederherzustellen.

**Microsoft Edge-Entwicklertools für UWP-JavaScript-Apps aktivieren (experimentell)** : Aktiviert Entwicklertools für UWP-JavaScript-apps in Microsoft Edge.

**Legacy-Chrome-JavaScript-Debugger für ASP.NET aktivieren**: Aktiviert den Legacy-Chrome-JavaScript-Skript Debugger für ASP.net-apps. Bei der ersten Verwendung in Chrome müssen Sie sich möglicherweise beim Browser anmelden, um Chrome-Erweiterungen zu aktivieren, die Sie installiert haben.

**Bei der Ausführung von Visual Studio als Administrator experimentelle Möglichkeit zum Starten des Chrome-JavaScript-Debuggens verwenden**: Weist Visual Studio an, eine neue Methode zum Starten von Chrome während des JavaScript-Debuggens auszuprobieren.

**DLL-Exporte laden (nur native)** : Lädt DLL‑Exporttabellen. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.

Verwenden Sie `dumpbin /exports`, um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](/cpp/build/reference/dash-exports).

**Diagramm mit parallelen Stapeln von unten nach oben anzeigen**: Steuert die Richtung, in der Stapel im Fenster **Parallele Stapel** angezeigt werden.

**Ausnahmen für den GPU-Speicherzugriff ignorieren, wenn der Wert durch die geschriebenen Daten nicht geändert wurde**: Ignoriert Racebedingungen, die während des Debuggens erkannt wurden, wenn sich die Daten nicht geändert haben. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).

**Verwalteten Kompatibilitätsmodus verwenden**: Ersetzt die Standarddebug-Engine durch eine Legacyversion, um die folgenden Szenarien zu ermöglichen:

- Sie verwenden eine andere .NET Framework Sprache als C#, Visual Basic oder F# , die eine eigene Ausdrucks Auswertung bereitstellt (einschließlich C++/CLI).

- Sie möchten "Bearbeiten und Fortfahren" C++ für Projekte während des Debuggens im gemischten Modus aktivieren.

> [!NOTE]
> Wenn Sie den verwalteten Kompatibilitätsmodus auswählen, werden einige Funktionen deaktiviert, die nur im standarddebugmodul implementiert werden. Die Legacy-debuggingengine wurde in Visual Studio 2012 ersetzt.

**Die älteren C#- and VB-Ausdrucksauswertungen verwenden**: Der Debugger verwendet anstelle von Visual C# Studio 2015 Roslyn-basierten Ausdrucks auswergratoren die Ausdrucks Auswertung Visual Studio 2013 oder Visual Basic.

**Warnen, wenn benutzerdefinierte Debugger für die Anzeige potenziell unsicherer Prozesse verwendet werden (nur verwaltet)** : Visual Studio warnt Sie bei Verwendung einer benutzerdefinierten Debuggerschnellansicht, die im zu debuggenden Prozess Code ausführt, da es sich um unsicheren Code handeln könnte.

**Debugging-Heapzuweisung von Windows verwenden (nur nativ)** : Aktiviert den Debugheap von Windows, um die Heapdiagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.

**UI-Debugtools für XAML aktivieren**: Die Fenster „Visuelle Echtzeitstruktur“ und „Echtzeit-Eigenschaften-Explorer“ werden angezeigt, wenn Sie mit dem Debuggen eines unterstützten Projekttyps beginnen (**F5**). Weitere Informationen finden Sie unter über [Prüfen von XAML-Eigenschaften beim Debuggen](../debugger/inspect-xaml-properties-while-debugging.md).

- **Voransicht für ausgewählte Elemente in der visuellen Echtzeitstruktur anzeigen**:   Das XAML-Element, dessen Kontext ausgewählt ist, ist auch im Fenster **Visuelle Echtzeitstruktur** ausgewählt.

- **Laufzeittools in Anwendung anzeigen**: Zeigt die Befehle der **visuellen Live** Struktur in einer Symbolleiste im Hauptfenster der XAML-Anwendung an, die gedebuggt wird. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt.

- **XAML-Hot-Neuladen aktivieren**: Ermöglicht die Verwendung der XAML-Funktion "Hot-Upload" mit XAML-Code, wenn Ihre APP ausgeführt wird. (Diese Funktion wurde zuvor als "XAML-Bearbeitung und Fortfahren" bezeichnet.)

**Diagnosetools beim Debuggen aktivieren**: Das Fenster **Diagnosetools** wird während des Debuggens angezeigt.

**PerfTip für verstrichene Zeit beim Debuggen anzeigen**: Das Codefenster zeigt an, wie viel Zeit bei einem bestimmten Methodenaufruf während des Debuggens verstrichen ist.

**„Bearbeiten und Fortfahren“ aktivieren**: Aktiviert die Funktion "Bearbeiten und Fortfahren" beim Debuggen.

- **natives Bearbeiten und Fortfahren aktivieren**: Sie können die Funktion „Bearbeiten und Fortfahren“ während des Debuggens von systemeigenem C++-Code verwenden. Weitere Informationen finden Sie unter " [Bearbeiten und Fortfahren C++" (Visual)](../debugger/edit-and-continue-visual-cpp.md).

- **Änderungen beim Fortfahren anwenden (nur nativ)** : Beim Fortsetzen eines unterbrochenen Prozesses kompiliert Visual Studio automatisch alle ausstehenden Codeänderungen und wendet sie an. Ist diese Option nicht aktiviert, können Sie Änderungen mit der Option **Codeänderungen übernehmen** im Menü **Debuggen** übernehmen.

- **Warnung bei veraltetem Code (nur nativ)** :   Ruft Warnungen über veralteten Code ab.

**Schaltfläche "Ausführen bis Klick" im Editor beim Debuggen anzeigen**: Wenn diese Option ausgewählt ist, wird die Schaltfläche [Ausführen bis klicken](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) beim Debuggen angezeigt.

**Konsole beim Beenden des Debuggings automatisch schließen**: Weist Visual Studio an, die Konsole am Ende einer Debugsitzung zu schließen.

::: moniker range=">= vs-2019" 
**Schnelle Ausdrucks Auswertung aktivieren (nur verwaltet)** : Ermöglicht dem Debugger, eine schnellere Auswertung durch die Simulation der Ausführung einfacher Eigenschaften und Methoden zu versuchen.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>In älteren Versionen von Visual Studio verfügbare Optionen

Wenn Sie eine ältere Version von Visual Studio verwenden, sind möglicherweise einige zusätzliche Optionen vorhanden.

**Ausnahmen-Assistent aktivieren**: Für verwalteten Code aktiviert den Ausnahmen-Assistenten. Ab Visual Studio 2017 hat das Exception-Hilfsprogramm den Ausnahmen-Assistenten ersetzt.

**Aufrufliste für Ausnahmefehler entladen**: Führt dazu, dass das Fenster **Aufrufliste** die Aufrufliste an den Punkt zurücksetzt, bevor der Ausnahmefehler aufgetreten ist.

**Warnung, wenn keine Symbole beim Starten gefunden werden (nur nativ)** : Zeigt ein Warn Dialogfeld an, wenn Sie ein Programm debuggen, für das der Debugger keine Symbol Informationen hat.

**Warnung, wenn Skriptdebugging beim Start deaktiviert ist**: Zeigt ein Warnungsdialogfeld an, wenn der Debugger mit deaktiviertem Skriptdebuggen gestartet wird.

**nativen Kompatibilitätsmodus verwenden**: Wenn diese Option ausgewählt ist, wird der native Debugger von Visual Studio 2010 anstelle des neuen nativen Debuggers verwendet.

- Verwenden Sie diese Option, wenn Sie .net C++ -Code Debuggen, da das neue Debugmodul C++ das Auswerten von .net-Ausdrücken nicht unterstützt. Durch das Aktivieren des systemeigenen Kompatibilitätsmodus werden aber viele Features deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. Beispielsweise fehlen in der Legacy-Engine viele Visualisierungen für integrierte Typen wie `std::string` in Visual Studio 2015-Projekten.   Verwenden Sie Visual Studio 2013-Projekte für die optimale debuggingdarstellung in diesen Fällen.

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
