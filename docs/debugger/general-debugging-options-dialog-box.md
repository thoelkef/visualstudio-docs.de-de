---
title: Allgemein, Debugging, Options-Dialogfeld | Microsoft Docs
ms.date: 11/12/2019
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
ms.openlocfilehash: 98bbd65d11b26d9b35000e4acbe4d28a585f8ddc
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472697"
---
# <a name="general-debugging-options"></a>Allgemeine Debugging-Optionen

Um Visual Studio-Debuggeroptionen festzulegen, wählen Sie > **Extras-Optionen**aus, und wählen Sie unter **Debuggen** die Felder neben den **Allgemeinen** Optionen aus oder deaktivieren Sie die Option. **Tools** Sie können alle Standardeinstellungen mit **Tools** > **Import und Export Settings** > **Alle Einstellungen zurücksetzen**wiederherstellen. Um eine Teilmenge der Einstellungen zurückzusetzen, speichern Sie Ihre Einstellungen mit dem Assistenten zum Importieren und Exportieren von **Einstellungen,** bevor Sie die Änderungen vornehmen, die Sie testen möchten, und importieren Sie anschließend die gespeicherten Einstellungen.

Sie können die folgenden **allgemeinen** Optionen festlegen:

**Fragen Sie vor dem Löschen aller Haltepunkte:** Erfordert eine Bestätigung, bevor Sie den Befehl **Alle Haltepunkte löschen** abschließen.

**Alle Prozesse unterbrechen, wenn ein Prozess unterbrochen**wird: Gleichzeitig werden alle Prozesse unterbrochen, an die der Debugger angefügt ist, wenn eine Unterbrechung auftritt.

**Unterbrechen, wenn Ausnahmen AppDomain- oder verwaltete/systemeigene Grenzen überschreiten:** Beim Debuggen mit verwalteter oder gemischter Sprache kann die Common Language-Laufzeit Ausnahmen abfangen, die Anwendungsdomänengrenzen oder verwaltete/systemeigene Grenzen überschreiten, wenn die folgenden Bedingungen zutreffen:

1. Wenn in nativem Code verwalteter Code mit COM-Interop aufgerufen wird und im verwalteten Code eine Ausnahme ausgelöst wird. Siehe [Einführung in COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Wenn verwalteter Code, der in der Anwendungsdomäne 1 ausgeführt wird, verwalteten Code in der Anwendungsdomäne 2 aufruft und der Code in Anwendungsdomäne 2 eine Ausnahme auslöst. Siehe [Programmieren mit Anwendungsdomänen](/dotnet/articles/framework/app-domains/index).

3. Wenn Code eine Funktion mithilfe von Reflektion aufruft, löst diese Funktion eine Ausnahme aus. Siehe [Reflexion](/dotnet/framework/reflection-and-codedom/reflection).

In den Bedingungen 2 und 3 wird die `mscorlib` Ausnahme manchmal von verwaltetem Code in anstatt von der Common Language Runtime abgefangen. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.

**Debuggen auf Adressebene aktivieren:** Aktiviert erweiterte Funktionen für das Debuggen auf Adressebene (das **Demontagefenster,** das **Fenster Register** und Adresshaltepunkte).

- **Demontage anzeigen, wenn die Quelle nicht verfügbar ist:** Zeigt automatisch das **Demontagefenster** an, wenn Sie Code debuggen, für den die Quelle nicht verfügbar ist.

**Haltepunktfilter aktivieren:** Ermöglicht das Festlegen von Filtern für Haltepunkte, sodass sie nur bestimmte Prozesse, Threads oder Computer betreffen.

**Verwenden sie den neuen Ausnahmehilfsprogramm**: Aktiviert den Ausnahmehilfsprogramm, das den Ausnahmeassistenten ersetzt. (Exception Helper wird ab Visual Studio 2017 unterstützt)

> [!NOTE]
> Für verwalteten Code wurde diese Option zuvor als **Ausnahmeassistent** aktivieren aufgerufen.

**Nur meinen Code aktivieren**: Der Debugger wird nur in Benutzercode ("Mein Code") angezeigt und schrittweise ausgeführt, wobei Systemcode und anderer Code ignoriert werden, der optimiert ist oder über keine Debugsymbole verfügt.

- **Warnen, wenn beim Start kein Benutzercode**vorhanden ist (nur verwaltet): Wenn das Debuggen mit aktiviertem "Nur mein Code" beginnt, werden Sie mit dieser Option gewarnt, wenn kein Benutzercode vorhanden ist ("Mein Code").

**.NET Framework-Quellschritt aktivieren**: Ermöglicht dem Debugger den Schritt in die .NET Framework-Quelle. Wenn Sie diese Option aktivieren, wird Just My Code automatisch deaktiviert. .NET Framework-Symbole werden an einen Cachespeicherort heruntergeladen. Ändern Sie den Cachespeicherort mit dem Dialogfeld **Optionen,** **Seite Debugging-Kategorie,** **Symbole.**

**Schritt über Eigenschaften und Operatoren (nur verwaltet):** Verhindert, dass der Debugger in Eigenschaften und Operatoren im verwalteten Code tritt.

**Eigenschaftenauswertung und andere implizite Funktionsaufrufe aktivieren:** Aktiviert die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in Variablenfenstern und im **QuickWatch-Dialogfeld.**

- **Zeichenfolgenkonvertierungsfunktion für Objekte in Variablenfenstern aufrufen (nur C- und JavaScript)**: Führt einen impliziten Zeichenfolgenkonvertierungsaufruf aus, wenn Objekte in Variablenfenstern ausgewertet werden. Das Ergebnis wird als Zeichenfolge anstelle des Typnamens angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann vom DebuggerDisplay-Attribut überschrieben werden (siehe [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)).

**Quellserverunterstützung aktivieren:** Weist den Visual Studio-Debugger an, Quelldateien von`srcsrv.dll`Quellservern abzurufen, die das SrcSrv- ( )-Protokoll implementieren. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen zum SrcSrv-Setup finden Sie in der [SrcSrv-Dokumentation.](/windows-hardware/drivers/debugger/srcsrv) Weitere Informationen finden Sie unter [Symbol (.pdb) und Quelldateien angeben](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Da das Lesen von *PDB-Dateien* beliebigen Code in den Dateien ausführen kann, stellen Sie sicher, dass Sie dem Server vertrauen.

- **Diagnosemeldungen des Druckquellservers in das Ausgabefenster:** Wenn die Quellserverunterstützung aktiviert ist, wird die Diagnoseanzeige mit dieser Einstellung aktiviert.

- **Quellserver für teilweise Vertrauensassemblys zulassen (nur verwaltet):** Wenn die Quellserverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten des Nichtabrufens von Quellen für teilweise vertrauensvolle Assemblys.

- **Führen Sie immer nicht vertrauenswürdige Quellserverbefehle ohne Aufforderung**aus: Wenn die Quellserverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten der Eingabeaufforderung beim Ausführen eines nicht vertrauenswürdigen Befehls.

**Source Link-Unterstützung aktivieren**: Weist den Visual Studio-Debugger an, Quelldateien für *PDB-Dateien* herunterzuladen, die Quellverknüpfungsinformationen enthalten. Weitere Informationen zu Source Link finden Sie in der [Quelllinkspezifikation](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Da Source Link Dateien mit http oder https herunterlädt, stellen Sie sicher, dass Sie der *.pdb-Datei* vertrauen.

- **Zurückfall zur Git Credential Manager-Authentifizierung für alle Quellverknüpfungsanforderungen:** Wenn die Quellverknüpfungsunterstützung aktiviert ist und eine Quellverknüpfungsanforderung die Authentifizierung fehlschlägt, ruft Visual Studio dann den Git Credential Manager auf.

**Markieren Sie die gesamte Zeile für Haltepunkte und die aktuelle Anweisung (nur C++):** Wenn der Debugger einen Haltepunkt oder eine aktuelle Anweisung hervorhebt, wird die gesamte Zeile hervorgehoben.

**Quelldateien benötigen, damit sie genau mit der ursprünglichen Version übereinstimmen:** Weist den Debugger an, zu überprüfen, ob eine Quelldatei mit der Version des Quellcodes übereinstimmt, der zum Erstellen der ausführbaren Datei verwendet wird, die Sie debuggen. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert, eine passende Quelle zu finden. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt.

**Leiten Sie den gesamten Ausgabefenstertext in das Direktfenster**um: Sendet alle Debuggermeldungen, die normalerweise im **Ausgabefenster** angezeigt werden, an das **Direktfenster.**

**Rohstruktur von Objekten in Variablenfenstern anzeigen**: Deaktiviert alle Objektstrukturansichtsanpassungen. Weitere Informationen zu Ansichtsanpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten verwalteter Objekte](../debugger/create-custom-views-of-managed-objects.md).

**JIT-Optimierung bei Modullast unterdrücken (nur verwaltet):** Deaktiviert die JIT-Optimierung von verwaltetem Code, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt wird. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird. Weitere Informationen finden Sie unter [JIT-Optimierung und Debuggen](../debugger/jit-optimization-and-debugging.md).

**JavaScript-Debugging für ASP.NET (Chrome, Microsoft Edge und IE) aktivieren:** Aktiviert den Skriptdebugger für ASP.NET Apps. Bei der ersten Verwendung in Chrome müssen Sie sich möglicherweise beim Browser anmelden, um die installierten Chrome-Erweiterungen zu aktivieren. Deaktivieren Sie diese Option, um zum Legacyverhalten zurückzukehren.

**Edge Developer Tools für UWP JavaScript Apps (Experimental) aktivieren:** Aktiviert Entwicklertools für UWP JavaScript-Apps in Microsoft Edge.

**Legacy-Chrome JavaScript-Debugger für ASP.NET aktivieren:** Aktiviert den älteren Chrome JavaScript-Skriptdebugger für ASP.NET Apps. Bei der ersten Verwendung in Chrome müssen Sie sich möglicherweise beim Browser anmelden, um die installierten Chrome-Erweiterungen zu aktivieren.

**Verwenden Sie die experimentelle Möglichkeit, um Chrome JavaScript-Debugging zu starten, wenn Sie Visual Studio als Administrator ausführen:** Weist Visual Studio an, eine neue Möglichkeit zum Starten von Chrome während des JavaScript-Debuggens zu versuchen.

**DLL-Exporte laden (nur Nativ):** Lädt dLL-Exporttabellen. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.

Verwenden Sie `dumpbin /exports`, um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](/cpp/build/reference/dash-exports).

**Parallelstacks-Diagramm von unten nach oben anzeigen**: Steuert die Richtung, in der Stapel im Fenster Parallel **Stacks** angezeigt werden.

**Ignorieren Sie GPU-Speicherzugriffsausnahmen, wenn die geschriebenen Daten den Wert nicht geändert haben:** Ignoriert Racebedingungen, die während des Debuggens erkannt wurden, wenn sich die Daten nicht geändert haben. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).

**Managed Compatibility Mode verwenden**: Ersetzt das Standarddebugmodul durch eine ältere Version, um die folgenden Szenarien zu aktivieren:

- Sie verwenden eine andere .NET-Sprache als C- oder Visual Basic oder F,die einen eigenen Ausdrucksauswertungswertor bereitstellt (einschließlich C++/CLI).

- Sie möchten Bearbeiten und Fortfahren für C++-Projekte während des Debuggens im gemischten Modus aktivieren.

> [!NOTE]
> Wenn Sie den Modus "Verwaltete Kompatibilität" auswählen, werden einige Features deaktiviert, die nur im Standarddebugmodul implementiert sind. Das ältere Debuggingmodul wurde in Visual Studio 2012 ersetzt.

Verwenden Sie die Legacy-Auswertungen für **C- und VB-Ausdruckswerte:** Der Debugger verwendet die Visual Studio 2013-Code- oder Visual Basic-Ausdrucksauswertungen anstelle der Roslyn-basierten Ausdrucksauswertungen von Visual Studio 2015.

**Warnung bei Verwendung benutzerdefinierter Debugger-Visualisierungen vor potenziell unsicheren Prozessen (nur verwaltet)**: Visual Studio warnt Sie, wenn Sie eine benutzerdefinierte Debugger-Visualisierung verwenden, die Code im debuggenProzess ausführt, da es möglicherweise unsicheren Code ausführt.

**Windows-Debugheap-Allokator aktivieren (nur Nativ):** Aktiviert den Windows-Debugheap, um die Heapdiagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.

**UI-Debugging-Tools für XAML aktivieren:** Die Live Visual Tree und die Live Property Explore-Fenster werden angezeigt, wenn Sie mit dem Debuggen (**F5**) eines unterstützten Projekttyps beginnen. Weitere Informationen finden Sie unter Überprüfen von [XAML-Eigenschaften beim Debuggen](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Vorschau ausgewählter Elemente in Live Visual Tree**: Das XAML-Element, dessen Kontext ausgewählt ist, wird auch im Fenster **"Visuelle "Live"-Struktur** ausgewählt.

- **Laufzeittools in der Anwendung anzeigen**: Zeigt die Live Visual **Tree-Befehle** in einer Symbolleiste im Hauptfenster der XAML-Anwendung an, die gedebuggt wird. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt.

- **XAML Hot Reload aktivieren**: Ermöglicht die Verwendung der XAML Hot Reload-Funktion mit XAML-Code, wenn Ihre App ausgeführt wird. (Diese Funktion wurde zuvor als "XAML Bearbeiten und Fortfahren" bezeichnet.)

::: moniker range=">= vs-2019" 
- **Just My XAML aktivieren**: Ab Visual Studio 2019 Version 16.4 zeigt die **Live Visual Tree** standardmäßig nur XAML an, das als Benutzercode klassifiziert ist. Wenn Sie diese Option deaktivieren, wird der gesamte generierte XAML-Code im Tool angezeigt.

- **Deaktivieren des Auswahlmodus, wenn ein Element ausgewählt ist** Ab Visual Studio 2019 Version 16.4 schaltet sich die Schaltfläche für die In-App-Symbolleistenelementauswahl (**Auswahl aktivieren**) aus, wenn ein Element ausgewählt ist. Wenn Sie diese Option deaktivieren, bleibt die Elementauswahl so lange erhalten, bis Sie erneut auf die Schaltfläche in der App-Symbolleiste klicken.
::: moniker-end

**Diagnosetools beim Debuggen aktivieren:** Das Fenster **Diagnosetools** wird beim Debuggen angezeigt.

**Verstrichene Zeit perfTip beim Debuggen anzeigen:** Das Codefenster zeigt die verstrichene Zeit eines bestimmten Methodenaufrufs beim Debuggen an.

**Bearbeiten und Fortfahren aktivieren**: Aktiviert die Funktion Bearbeiten und Fortfahren während des Debuggens.

- **Native Bearbeiten und Fortfahren aktivieren**: Sie können die Funktion Bearbeiten und Fortfahren verwenden, während Sie nativen C++-Code debuggen. Weitere Informationen finden Sie [unter Bearbeiten und Fortfahren (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Änderungen auf weiter anwenden (nur Nativ:** Visual Studio kompiliert automatisch alle ausstehenden Codeänderungen, die Sie beim Fortsetzen des Prozesses aus einem Unterbrechungsstatus vorgenommen haben. Wenn diese Option nicht ausgewählt ist, können Sie Änderungen mithilfe des Elements **Codeänderungen anwenden** im Menü **Debugverwenden** anwenden.

- **Warnung vor veraltetem Code (nur Native)**: Erhalten Sie Warnungen über veralteten Code.

**Schaltfläche "Ausführen auf Klick" im Editor beim Debuggen**anzeigen: Wenn diese Option ausgewählt ist, wird die Schaltfläche "Auf [Klicken ausführen"](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) während des Debuggens angezeigt.

**Automatisches Schließen der Konsole beim Beenden des Debuggens:** Weist Visual Studio an, die Konsole am Ende einer Debugsitzung zu schließen.

::: moniker range=">= vs-2019"
**Schnelle Ausdrucksauswertung aktivieren (nur verwaltet):** Ermöglicht dem Debugger, eine schnellere Auswertung zu versuchen, indem die Ausführung einfacher Eigenschaften und Methoden simuliert wird.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Verfügbare Optionen in älteren Versionen von Visual Studio

Wenn Sie eine ältere Version von Visual Studio verwenden, sind möglicherweise einige zusätzliche Optionen vorhanden.

**Ausnahmeassistent aktivieren**: Für verwalteten Code wird der Ausnahmeassistent aktiviert. Ab Visual Studio 2017 hat der Ausnahmehelfer den Ausnahmeassistenten ersetzt.

**Auflösen der Aufrufliste für nicht behandelte Ausnahmen:** Bewirkt, dass das **Aufruflistenfenster** die Aufrufliste auf den Punkt zurückführt, bevor die nicht behandelte Ausnahme aufgetreten ist.

**Warnen, wenn beim Start keine Symbole angezeigt werden (nur nativ):** Zeigt ein Warndialogfeld an, wenn Sie ein Programm debuggen, für das der Debugger keine Symbolinformationen hat.

**Warnung, wenn das Skriptdebuggen beim Start deaktiviert ist:** Zeigt ein Warndialogfeld an, wenn der Debugger mit deaktiviertem Skriptdebugging gestartet wird.

**Nativer Kompatibilitätsmodus verwenden:** Wenn diese Option ausgewählt ist, verwendet der Debugger den systemeigenen Debugger Visual Studio 2010 anstelle des neuen systemeigenen Debuggers.

- Verwenden Sie diese Option, wenn Sie .NET C++-Code debuggen, da das neue Debugmodul die Auswertung von .NET C++-Ausdrücken nicht unterstützt. Durch das Aktivieren des systemeigenen Kompatibilitätsmodus werden aber viele Features deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. Dem Legacymodul fehlen beispielsweise viele Visualisierungen für integrierte `std::string` Typen wie in Visual Studio 2015-Projekten.   Verwenden Sie Visual Studio 2013-Projekte für die optimale Debugerfahrung in diesen Fällen.

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Blick auf den Debugger](../debugger/debugger-feature-tour.md)
