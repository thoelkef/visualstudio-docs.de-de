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
ms.openlocfilehash: d3fa7ae62c19a7af45188bab08ce9b3144032b7d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72435706"
---
# <a name="general-debugging-options"></a>Allgemeine Debugoptionen

Um die Visual Studio-Debuggeroptionen festzulegen, wählen Sie Extras  > **Optionen**aus, und **Wählen Sie unter** **Debuggen** die Kontrollkästchen neben den **allgemeinen** Optionen aus. Sie können alle Standardeinstellungen mit **Tools**  > **Einstellungen importieren und exportieren**  > **alle Einstellungen zurücksetzen**. Wenn Sie eine Teilmenge der Einstellungen zurücksetzen möchten, speichern Sie Ihre Einstellungen mit dem **Assistenten zum Importieren und Exportieren von Einstellungen** , bevor Sie die Änderungen vornehmen, die Sie testen möchten, und importieren Sie anschließend die gespeicherten Einstellungen.

Sie können die folgenden **allgemeinen** Optionen festlegen:

**Vor dem Löschen aller Haltepunkte Fragen**: erfordert eine Bestätigung vor Abschluss des Befehls **delete all Haltepunkte** .

**Alle Prozesse anhalten, wenn ein Prozess unterbrochen**wird: unterbricht gleichzeitig alle Prozesse, an die der Debugger angefügt ist, wenn eine Unterbrechung auftritt.

Unter **brechen, wenn Ausnahmen Anwendungs Domänen-oder verwaltete/native Grenzen überschreiten**: beim Debuggen von verwaltetem oder gemischtem Modus können Common Language Runtime Ausnahmen abfangen, die Anwendungs Domänen Grenzen oder verwaltete/native Grenzen überschreiten, wenn Folgendes Bedingungen sind "true":

1. Wenn in nativem Code verwalteter Code mit COM-Interop aufgerufen wird und im verwalteten Code eine Ausnahme ausgelöst wird. Weitere Informationen finden [Sie unter Einführung in COM-Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Wenn verwalteter Code, der in der Anwendungsdomäne 1 ausgeführt wird, verwalteten Code in der Anwendungsdomäne 2 aufruft und der Code in Anwendungsdomäne 2 eine Ausnahme auslöst. Siehe [Programmieren mit Anwendungsdomänen](/dotnet/articles/framework/app-domains/index).

3. Wenn Code eine Funktion mit Reflektion aufruft und diese Funktion eine Ausnahme auslöst. Siehe [Reflektion](/dotnet/framework/reflection-and-codedom/reflection).

In den Bedingungen 2 und 3 wird die Ausnahme manchmal von verwaltetem Code in `mscorlib` und nicht vom Common Language Runtime abgefangen. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.

**Debugging auf Adress Ebene aktivieren**: aktiviert erweiterte Funktionen für das Debuggen auf Adress Ebene (das Fenster **Disassembly** , das Fenster " **Register** " und Adress Breakpoints).

- **Disassembly anzeigen, wenn Quelle nicht verfügbar ist**: zeigt das Disassemblyfenster automatisch an, wenn Sie Code Debuggen, für den die Quelle nicht verfügbar ist.

Halte **Punkt Filter aktivieren**: ermöglicht es Ihnen, Filter für Haltepunkte festzulegen, sodass Sie nur bestimmte Prozesse, Threads oder Computer beeinträchtigen.

**Die neue Ausnahmen-Hilfe verwenden**: aktiviert die Ausnahme-Hilfe, die den Ausnahmen-Assistenten ersetzt. (Ausnahmen-Hilfsprogramm wird ab Visual Studio 2017 unterstützt.)

> [!NOTE]
> Bei verwaltetem Code wurde diese Option zuvor als **enable the Exception Assistant** bezeichnet.

**Nur eigenen Code aktivieren**: der Debugger zeigt nur Benutzer Code ("mein Code") an und führt diesen Schritt aus. dabei werden System Code und anderer Code ignoriert, der optimiert ist oder keine Debugsymbole aufweist.

- **Warnung, wenn beim Starten kein Benutzercode ausgeführt wird (nur verwaltet)** : Wenn das Debuggen mit aktiviertem nur eigenen Code gestartet wird, werden Sie durch diese Option gewarnt, wenn kein Benutzercode ("mein Code") vorhanden ist.

Schrittweises **Aktivieren der .NET Framework Quelle**: ermöglicht dem Debugger, in .NET Framework Quelle zu wechseln. Wenn Sie diese Option aktivieren, wird nur eigenen Code automatisch deaktiviert. .NET Framework Symbole werden an einen Cache Speicherort heruntergeladen. Ändern Sie den Cache Speicherort, indem Sie das Dialogfeld **Optionen** , **debugkategorie** , **Symbol** Seite auswählen.

**Eigenschaften und Operatoren überspringen (nur verwaltet)** : verhindert, dass der Debugger die Eigenschaften und Operatoren in verwaltetem Code schrittweise durchlaufen wird.

Eigenschaften **Auswertung und andere implizite Funktionsaufrufe aktivieren: aktiviert**die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in den Variablen Fenstern und im Dialogfeld **schnell Überwachung** .

- **Zeichen folgen Konvertierungs Funktion für Objekte in Variablen FensternC# (und JavaScript)** : führt einen impliziten Zeichen folgen Konvertierungs-aufrufsbefehl beim Auswerten von Objekten in Variablen Fenstern aus. Das Ergebnis wird als Zeichenfolge anstelle des Typnamens angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann durch das Attribut "tbuggerdisplay" überschrieben werden (siehe [Verwenden des Attributs](../debugger/using-the-debuggerdisplay-attribute.md)"Debug-Display").

**Quell Serverunterstützung aktivieren**: weist den Visual Studio-Debugger an, Quelldateien von Quell Servern zu erhalten, die das SRCSRV-Protokoll (`srcsrv.dll`) implementieren. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen zum SrcSrv-Setup finden Sie in der [SRCSRV](/windows-hardware/drivers/debugger/srcsrv) -Dokumentation. Weitere Informationen finden Sie unter [Angeben von Symbol-(PDB-) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Da das Lesen von PDB-Dateien beliebigen Code in den Dateien ausführen kann, vergewissern Sie sich, dass Sie dem Server vertrauen können.

- **Diagnosemeldungen des Quell Servers im Ausgabefenster ausgeben**: Wenn die Quell Serverunterstützung aktiviert ist, aktiviert diese Einstellung die Diagnose Anzeige.

- **Quell Server für teilweise vertrauenswürdige Assemblys zulassen (nur verwaltet)** : Wenn die Quell Serverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten, bei dem keine Quellen für teilweise vertrauenswürdige Assemblys abgerufen werden.

- **Nicht vertrauenswürdige Quell Server Befehle immer ohne Aufforderung ausführen**: Wenn die Quell Serverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten der Eingabeaufforderung, wenn ein nicht vertrauenswürdiger Befehl ausgeführt wird.

**Unterstützung für Quell**Verknüpfungen aktivieren: weist den Visual Studio-Debugger an, Quelldateien für *PDB* -Dateien herunterzuladen, die Informationen zum quelllink enthalten. Weitere Informationen zum quelllink finden Sie in der [Spezifikation für den Quell Link](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
> Da der quelllink Dateien mithilfe von http oder HTTPS herunterlädt, sollten Sie sicherstellen, dass Sie der *PDB* -Datei vertrauen.

- **Fallback auf git Credential Manager-Authentifizierung für alle Quell**Verknüpfungs Anforderungen: Wenn die Unterstützung für Quell Verknüpfungen aktiviert ist und eine Quell Verknüpfungs Anforderung die Authentifizierung nicht besteht, ruft Visual Studio die git Credential Manager auf.

**Markieren Sie die gesamte Zeile für Haltepunkte und dieC++ aktuelle Anweisung (nur)** : Wenn der Debugger einen Breakpoint oder eine aktuelle Anweisung hervorhebt, wird die gesamte Zeile hervorgehoben.

**Quelldateien müssen exakt mit der Originalversion übereinstimmen**: weist den Debugger an, zu überprüfen, ob eine Quelldatei mit der Version des Quellcodes übereinstimmt, der zum Erstellen der ausführbaren Datei verwendet wird. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert, eine passende Quelle zu suchen. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt.

**Gesamten Text des Ausgabe Fensters an das direkt Fenster umleiten**: sendet alle Debugger-Nachrichten, die normalerweise im **Ausgabe** Fenster angezeigt werden, stattdessen an das **direkt** Fenster.

Unformatierte **Struktur von Objekten in Variablen Fenstern anzeigen**: deaktiviert alle Anpassungen der Objektstruktur Ansicht. Weitere Informationen zu Ansichts Anpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-dot-managed-objects.md).

**JIT-Optimierung beim Laden von Modulen unterdrücken (nur verwaltet)** : deaktiviert die JIT-Optimierung von verwaltetem Code, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt wird. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird. Weitere Informationen finden Sie unter [JIT-Optimierung und-Debuggen](../debugger/jit-optimization-and-debugging.md).

**JavaScript-Debuggen für ASP.net (Chrome, Edge und IE) aktivieren**: aktiviert den Skript Debugger für ASP.net-apps. Bei der ersten Verwendung in Chrome müssen Sie sich möglicherweise beim Browser anmelden, um Chrome-Erweiterungen zu aktivieren, die Sie installiert haben. Deaktivieren Sie diese Option, um das Legacy Verhalten wiederherzustellen.

**Edge-Entwicklertools für UWP-JavaScript-Apps aktivieren (experimentell)** : aktiviert Entwickler Tools für UWP-JavaScript-apps in Microsoft Edge.

**Legacy-Chrome-JavaScript-Debugger für ASP.net aktivieren**: aktiviert den Legacy-Chrome-JavaScript-Skript Debugger für ASP.net-apps. Bei der ersten Verwendung in Chrome müssen Sie sich möglicherweise beim Browser anmelden, um Chrome-Erweiterungen zu aktivieren, die Sie installiert haben.

**Verwenden Sie experimentelle Möglichkeiten zum Starten des Chrome-JavaScript-Debuggens beim Ausführen von Visual Studio als Administrator**: weist Visual Studio an, eine neue Möglichkeit zum Starten von Chrome beim JavaScript-Debugging zu

**DLL-Exporte laden (nur nativ)** : lädt DLL-Export Tabellen. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.

Verwenden Sie `dumpbin /exports`, um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](/cpp/build/reference/dash-exports).

**Diagramm "parallele Stapel Diagramm anzeigen**": steuert die Richtung, in der Stapel im Fenster " **parallele Stapel** " angezeigt werden.

**Ausnahmen für den GPU-Speicherzugriff ignorieren, wenn die geschriebenen Daten den Wert nicht geändert haben**: ignoriert Racebedingungen, die beim Debuggen erkannt wurden, wenn die Daten nicht geändert wurden. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).

**Verwalteten Kompatibilitätsmodus verwenden**: ersetzt das standarddebugmodul durch eine Legacy Version, um die folgenden Szenarien zu ermöglichen:

- Sie verwenden eine andere .NET Framework Sprache als C#, Visual Basic oder F# , die eine eigene Ausdrucks Auswertung bereitstellt (einschließlich C++/CLI).

- Sie möchten "Bearbeiten und Fortfahren" C++ für Projekte während des Debuggens im gemischten Modus aktivieren.

> [!NOTE]
> Wenn Sie den verwalteten Kompatibilitätsmodus auswählen, werden einige Funktionen deaktiviert, die nur im standarddebugmodul implementiert werden. Die Legacy-debuggingengine wurde in Visual Studio 2012 ersetzt.

**Verwenden der Legacy C# -und VB-Ausdrucks Auswertung**: der Debugger verwendet die Visual Studio 2013 C# -oder Visual Basic Ausdrucks Auswertung anstelle der Visual Studio 2015 Roslyn-basierten Ausdrucks Auswertung.

**Warnen, wenn benutzerdefinierte Debugger-Visualisierungen für potenziell unsichere Prozesse verwendet werden (nur verwaltet)** : Visual Studio warnt Sie, wenn Sie eine benutzerdefinierte Debugger-Schnellansicht verwenden, die im debuggten Prozess Code ausführt, da Sie unsicheren Code ausführen könnte. .

**Windows Debug Heap-Zuweisung aktivieren (nur nativ)** : aktiviert den Windows-Debugheap, um die Heap Diagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.

**UI-Debuggingtools für XAML aktivieren**: die Fenster visuelle echt Zeitstruktur und Live Eigenschaft durchsuchen werden angezeigt, wenn Sie das Debuggen (**F5**) eines unterstützten Projekt Typs starten. Weitere Informationen finden Sie unter über [Prüfen von XAML-Eigenschaften beim Debuggen](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Vorschau der ausgewählten Elemente in der visuellen**echt Zeitstruktur anzeigen: das XAML-Element, dessen Kontext ausgewählt ist, ist auch im Fenster " **visuelle** echt Zeitstruktur" ausgewählt.

- **Lauf Zeit Tools in Anwendung anzeigen**: zeigt die **visuellen Live** Strukturbefehle auf einer Symbolleiste im Hauptfenster der XAML-Anwendung an, die gedebuggt wird. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt.

- **XAML-Hot-Neuladen aktivieren**: ermöglicht Ihnen die Verwendung der XAML-Funktion "Hot Reload" mit XAML-Code, wenn Ihre APP ausgeführt wird. (Diese Funktion wurde zuvor als "XAML-Bearbeitung und Fortfahren" bezeichnet.)

**Diagnosetools während des Debuggens aktivieren**: das **Diagnosetools** Fenster wird angezeigt, während Sie Debuggen.

**Perftip für verstrichene Zeit beim Debuggen anzeigen**: im Code Fenster wird die verstrichene Zeit eines bestimmten Methoden Aufrufes beim Debuggen angezeigt.

" **Bearbeiten und Fortfahren" aktivieren**: aktiviert beim Debuggen die Funktion "Bearbeiten und fortfahren

- System eigenes **Bearbeiten und Fortfahren aktivieren**: Sie können die Funktion zum Bearbeiten und Fortfahren C++ beim Debuggen von nativem Code verwenden. Weitere Informationen finden Sie unter " [Bearbeiten und fortC++fahren" ()](../debugger/edit-and-continue-visual-cpp.md).

- **Änderungen beim Fortfahren anwenden (nur**System eigen): Visual Studio kompiliert automatisch alle ausstehenden Codeänderungen, die Sie vorgenommen haben, wenn der Prozess von einem unterbrechungzustand fortgesetzt wird. Ist diese Option nicht aktiviert, können Sie Änderungen mit der Option **Codeänderungen übernehmen** im Menü **Debuggen** übernehmen.

- **Warnung bei veraltetem Code (nur nativ)** : Warnungen zu veraltetem Code erhalten.

**Schaltfläche "Ausführen bis Klick" im Editor beim Debuggen anzeigen**: Wenn diese Option ausgewählt ist, wird die Schaltfläche " [Ausführen bis Klick](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) " beim Debuggen angezeigt.

Konsole beim Beenden des **Debuggens automatisch schließen**: weist Visual Studio an, die Konsole am Ende einer Debugsitzung zu schließen.

::: moniker range=">= vs-2019"
**Schnelle Ausdrucks Auswertung aktivieren (nur verwaltet)** : ermöglicht dem Debugger den Versuch, die Auswertung zu beschleunigen, indem einfache Eigenschaften und Methoden simuliert werden.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>In älteren Versionen von Visual Studio verfügbare Optionen

Wenn Sie eine ältere Version von Visual Studio verwenden, sind möglicherweise einige zusätzliche Optionen vorhanden.

**Aktivieren Sie den Ausnahmen-Assistenten**: aktiviert den Ausnahmen-Assistenten für verwalteten Code. Ab Visual Studio 2017 hat das Exception-Hilfsprogramm den Ausnahmen-Assistenten ersetzt.

Entladen **der aufrufsliste bei nicht behandelten Ausnahmen**: bewirkt, dass im Fenster " **aufrufsstapel** " ein Rollback der Rückruf Liste auf den Punkt ausgeführt wird, bevor die Ausnahme aufgetreten ist.

**Warnen, wenn beim Start keine Symbole angezeigt werden (nur**System eigen): zeigt ein Dialogfeld für Warnungen an, wenn Sie ein Programm debuggen, für das der Debugger keine Symbol Informationen hat.

Warnung, **Wenn Skript Debugging beim Start deaktiviert ist**: zeigt ein Warn Dialogfeld an, wenn der Debugger mit deaktiviertem Skript Debuggen gestartet wird.

Systemeigenen **Kompatibilitätsmodus verwenden**: Wenn diese Option ausgewählt ist, verwendet der Debugger den Visual Studio 2010 Native Debugger anstelle des neuen systemeigenen Debuggers.

- Verwenden Sie diese Option, wenn Sie .net C++ -Code Debuggen, da das neue Debugmodul C++ das Auswerten von .net-Ausdrücken nicht unterstützt. Durch das Aktivieren des systemeigenen Kompatibilitätsmodus werden aber viele Features deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. Beispielsweise fehlen in der Legacy-Engine viele Visualisierungen für integrierte Typen wie `std::string` in Visual Studio 2015-Projekten.   Verwenden Sie Visual Studio 2013-Projekte für die optimale debuggingdarstellung in diesen Fällen.

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
