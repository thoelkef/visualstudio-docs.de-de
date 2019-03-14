---
title: Allgemein, Debuggen, Dialogfeld "Optionen" | Microsoft-Dokumentation
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
ms.openlocfilehash: 2e97f2f844c53a6bf26fecc4559b65ae69970c6b
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526539"
---
# <a name="general-debugging-options"></a>Allgemeine Optionen für das Debuggen

Wählen Sie zum Festlegen von Optionen für Visual Studio-Debugger **Tools** > **Optionen**, und wählen Sie unter **Debuggen** aktivieren oder deaktivieren Sie die Kontrollkästchen neben den  **Allgemeine** Optionen. Sie können mit allen Standardeinstellungen wiederherstellen **Tools** > **Einstellungen importieren und exportieren** > **alle Einstellungen zurücksetzen**. Um eine Teilmenge der Einstellungen zurückzusetzen, speichern Sie die Einstellungen mit den **-Import- und Exportassistenten Einstellungen** vorzunehmende Änderungen, die Sie testen möchten, klicken Sie dann importieren Sie Ihre Einstellungen wurden gespeichert. anschließend.

Sie können festlegen, dass die folgenden **allgemeine** Optionen:

**Vor dem Löschen aller Haltepunkte Fragen**: erfordert eine Bestätigung vor dem Abschluss der **alle Haltepunkte löschen** Befehl.

**Alle Prozesse anhalten, wenn ein Prozess anhält**: unterbricht gleichzeitig auf alle Prozesse, die auf die der Debugger wird, angefügt, wenn eine Unterbrechung auftritt.

**Ausnahmen unterbrechen oder verwaltete/systemeigene Übergänge überschreitenden**: beim Debuggen von verwalteten oder gemischten Modus, die common Language Runtime kann Ausnahmen abfangen, die Grenzen von Anwendungsdomänen hinweg bei Anwendungsdomänengrenzen verwaltete/systemeigene Übergänge oder beim folgenden Bedingungen sind erfüllt:

1. Wenn in nativem Code verwalteter Code mit COM-Interop aufgerufen wird und im verwalteten Code eine Ausnahme ausgelöst wird. Finden Sie unter [Einführung in COM-Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Wenn verwalteter Code, der in der Anwendungsdomäne 1 ausgeführt wird, verwalteten Code in der Anwendungsdomäne 2 aufruft und der Code in Anwendungsdomäne 2 eine Ausnahme auslöst. Siehe [Programmieren mit Anwendungsdomänen](/dotnet/articles/framework/app-domains/index).

3. Wenn Code eine Funktion mithilfe der Reflektion aufgerufen, und diese Funktion löst eine Ausnahme aus. Finden Sie unter [Reflektion](/dotnet/framework/reflection-and-codedom/reflection).

Unter Umständen 2 und 3 wird die Ausnahme gelegentlich von verwaltetem Code in abgefangen `mscorlib` und nicht von der common Language Runtime. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.

**Debuggen auf Adressebene aktivieren**: Aktiviert erweiterte Funktionen für das Debuggen auf Adressebene (das **Disassembly** Fenster die **registriert** Fenster und Adresshaltepunkte).

- **Disassemblierung anzeigen, wenn die Quelle nicht verfügbar ist**: Zeigt automatisch die **Disassembly** Fenster beim Debuggen von Code für die die Quelle nicht verfügbar ist.

**Haltepunktfilter aktivieren**: können Sie Filter an Haltepunkten festlegen, sodass sie nur bestimmte Prozesse, Threads oder Computer gelten.

**Verwenden Sie das neue Ausnahmehilfsprogramm**: ermöglicht der Ausnahmen-Hilfe, die den Ausnahmen-Assistenten ersetzt. (Ausnahmen-Hilfe ist ab Visual Studio 2017 unterstützt)

> [!NOTE]
> Für verwalteten Code, der diese Option wurde bereits aufgerufen **Ausnahmen-Assistenten aktivieren** .

**Nur eigenen Code aktivieren**: der Debugger zeigt und die Schritte in Benutzercode ("Mein Code"), wird ignoriert, und anderen Code, der optimiert ist oder, die keine Debugsymbole.

- **Warnhinweis anzeigen, wenn kein Benutzercode beim Start (nur verwaltet)**: beim Starten des Debuggens mit nur mein Code aktiviert, diese Option warnt Sie, wenn kein Benutzercode ("Mein Code") vorhanden ist.

**Aktivieren von .NET Framework-Quellcodes**: ermöglicht dem Debugger mit Einzelschritten, .NET Framework-Quelle. Automatisch durch Aktivieren dieser Option wird nur mein Code deaktiviert. .NET Framework-Symbole werden an einen Cachespeicherort heruntergeladen. Ändern des cachespeicherorts mit der **Optionen** Dialogfeld **Debuggen** Kategorie **Symbole** Seite.

**Prozedurschritt für Eigenschaften und Operatoren überspringen (nur verwaltet)**: verhindert, dass den Debugger Eigenschaften und Operatoren in verwaltetem Code schrittweise.

**Eigenschaftenauswertung und andere implizite Funktionsaufrufe**: aktiviert die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in Variablenfenstern und **Schnellüberwachung** Dialogfeld.

- **Zeichenfolgenkonvertierungsfunktion für Objekte in Variablenfenstern aufrufen (C# nur und JavaScript)**: führt Sie einen impliziten Zeichenkonvertierungsaufruf beim Auswerten von Objekten in Variablenfenstern. Das Ergebnis wird als eine Zeichenfolge anstatt in der Typname angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann vom DebuggerDisplay-Attribut überschrieben werden (siehe [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)).

**Quellserverunterstützung aktivieren**: weist den Visual Studio-Debugger an Quelldateien von Quellservern abzurufen, die das SrcSrv implementieren (`srcsrv.dll`) Protokoll. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen zum SrcSrv-Setup finden Sie unter den [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) Dokumentation. Darüber hinaus finden Sie unter [angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Da das Lesen von PDB-Dateien beliebigen Code in den Dateien ausführen kann, vergewissern Sie sich, dass Sie dem Server vertrauen können.

- **Source Server-diagnosemeldungen im Ausgabefenster Drucken**: Wenn die quellserverunterstützung aktiviert ist, aktiviert diese Einstellung die diagnostische Anzeige.

- **Quellserver für teilweise vertrauenswürdige Assemblys (nur verwaltet) zulassen**: Wenn die quellserverunterstützung aktiviert ist, wird diese Einstellung überschreibt das Standardverhalten beim Nichtabrufen von Quellen für teilweise vertrauenswürdige Assemblys.

- **Immer nicht vertrauenswürdigen Quellserverbefehle ohne Aufforderung ausführen**: Wenn die quellserverunterstützung aktiviert ist, wird diese Einstellung überschreibt das Standardverhalten von eingabeaufforderungen festzulegen, wenn es sich bei einen nicht vertrauenswürdigen Befehl ausführen.

**Quelllinkunterstützung aktivieren**: weist den Visual Studio-Debugger zum Herunterladen der Quelldateien für *PDB* Dateien, die Informationen der Link "Quelle" enthalten. Weitere Informationen zu den Link "Quelle", finden Sie unter den [quellenspezifikation-Verknüpfung](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
>  Da der Link "Quelle" werden Dateien, die über http oder Https heruntergeladen haben, stellen Sie sicher, dass Sie vertrauen den *PDB* Datei.

- **Reduzierung auf Git Credential Manager-Authentifizierung für alle Anforderungen für Quelllinks**: Wenn quelllinkunterstützung aktiviert ist und eine Link "Quelle"-Anforderung schlägt fehl, Authentifizierung, Visual Studio und Git Credential Manager aufruft.

**Bei Haltepunkten und aktueller Anweisung (nur C++) die gesamte Zeile markieren**: Wenn der Debugger einen Haltepunkt oder die aktuelle Anweisung hervorhebt, werden die gesamte Zeile hervorgehoben.

**Quelldateien müssen genau mit übereinstimmen, die ursprüngliche Version**: weist den Debugger, um sicherzustellen, dass eine Quelldatei mit der Version des Quellcodes verwendet, um die ausführbare Datei zu erstellen, Sie Debuggen, übereinstimmt. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert, eine übereinstimmende Quelle zu suchen. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt.

**Gesamten Text aus Ausgabefenster an das Direktfenster umleiten**: sendet alle Debuggermeldungen, die normalerweise in der **Ausgabe** Fenster aus, um die **direkt** Fenster stattdessen.

**Unformatierte Struktur von Objekten in Variablenfenstern anzeigen**: deaktiviert alle objektstrukturansichten. Weitere Informationen zu ansichtsanpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-dot-managed-objects.md).

**JIT-Optimierung beim Laden von Modulen (nur verwaltet) unterdrücken**: deaktiviert die JIT-Optimierung von verwaltetem Code aus, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt ist. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird. Weitere Informationen finden Sie unter [JIT-Optimierung und-Debuggen](../debugger/jit-optimization-and-debugging.md).

**Aktivieren Sie JavaScript-debugging für ASP.NET (Chrome, Edge und IE)**: ermöglicht es den Skriptdebugger für ASP.NET-Apps. Bei der ersten Verwendung in Chrome müssen Sie sich in den Browser Chrome-Erweiterungen zu aktivieren, die Sie installiert haben. Deaktivieren Sie diese Option, um zum alten Verhalten zurückzukehren.

**Aktivieren Sie Microsoft Edge-Entwicklertools für UWP-JavaScript-Apps (experimentell)**: ermöglicht die Entwicklertools für UWP-JavaScript-apps in Microsoft Edge.

**Aktivieren von legacy-Chrome-JavaScript-Debugger für ASP.NET**: kann den legacy-Chrome-JavaScript-Skriptdebugger für ASP.NET-Apps. Bei der ersten Verwendung in Chrome müssen Sie sich in den Browser Chrome-Erweiterungen zu aktivieren, die Sie installiert haben.

**Verwenden Sie die experimentelle Möglichkeit zum Starten, wenn Visual Studio als Administrator ausführen Chrome-JavaScript-debugging**: teilt Visual Studio eine neue Möglichkeit zum Starten von Chrome während des Debuggens von JavaScript zu testen.

**(Nur systemeigen) der Dll-Exporte laden**: Dll-Exporttabellen lädt. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.

Verwenden Sie `dumpbin /exports`, um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](/cpp/build/reference/dash-exports).

**Show parallelen Stapeln von unten nach oben im Diagramm**: steuert die Richtung, in der Stapel, in angezeigt werden, der **parallele Stapel** Fenster.

**GPU Ausnahmen Speicherzugriff ignorieren, wenn die geschriebenen Daten nicht geändert haben**: ignoriert Racebedingungen, die erkannt wurden, während des Debuggens, wenn die Daten nicht geändert haben. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).

**Verwenden verwalteter Kompatibilitätsmodus**: ersetzt das standarddebugmodul durch eine Legacyversion, um diese Szenarien zu ermöglichen:

- Verwenden Sie .NET Framework-Sprache außer C#, Visual Basic oder F# , einen eigenen Expression Evaluator bereitstellt (Dies schließt C++ / CLI).

- Sie möchten bearbeiten und Fortfahren für C++-Projekte beim Debuggen im gemischten Modus aktivieren.

> [!NOTE]
> Auswählen des verwalteten Kompatibilitätsmodus deaktiviert Modus einige Features, die nur im standardmäßigen Debugmodul implementiert werden. Im Visual Studio 2012 wurde die Legacyversion des Debugmoduls ersetzt.

**Verwenden Sie die Vorgängerversion C# und VB-ausdrucksauswertungen**: der Debugger verwendet Visual Studio 2013 C# oder VB-ausdrucksauswertungen anstelle der Visual Studio 2015 Roslyn-basierten ausdrucksauswertungen.

**Warnen, wenn benutzerdefinierte Debugger für die Anzeige potenziell unsicherer Prozesse (nur verwaltet) mit**: Visual Studio warnt Sie bei Verwendung eine benutzerdefinierten Debuggerschnellansicht, die Code, im gedebuggten Prozess ausgeführt wird, weil auf ihm ausgeführt werden konnte unsicherer Code.

**Heapzuweisung von Windows Debug (nur systemeigen)**: ermöglicht den Windows-Debugheap, um die heapdiagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.

**Aktivieren von UI-Debuggingtools für XAML**: der Live Visual Tree und die Live-Eigenschaften-Explorer-Fenster werden angezeigt, wenn Sie das Debuggen starten (**F5**) eines unterstützten Projekttyps. Weitere Informationen finden Sie unter [Überprüfen von XAML-Eigenschaften während des Debuggens](../debugger/inspect-xaml-properties-while-debugging.md).

- **Vorschau der ausgewählten Elemente in visuelle Echtzeitstruktur**: der XAML-Element, dessen Kontext ausgewählt ist, ebenfalls ausgewählt ist, der **Live Visual Tree** Fenster.

- **Laufzeittools in Anwendung**: Zeigt die **Live Visual Tree** Befehle in einer Symbolleiste des Hauptfensters der XAML-Anwendung, die gedebuggt wird. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt.

- **XAML bearbeiten und Fortfahren aktivieren**: ermöglicht es Ihnen, verwenden die Bearbeitung und Fortsetzen von XAML-Code-Funktion.

**Aktivieren der Diagnosetools während des Debuggens**: die **Diagnosetools** Fenster wird angezeigt, während des Debuggens.

**PerfTip für verstrichene Zeit beim Debuggen anzeigen**: das Codefenster zeigt der verstrichenen Zeit für einen bestimmten Methodenaufruf während des Debuggens.

**Bearbeiten und Fortfahren aktivieren**: ermöglicht die bearbeiten und Fortfahren-Funktionalität während des Debuggens.

- **Bearbeiten und Fortfahren aktivieren**: Sie verwenden, bearbeiten und fortfahren, Funktionen während des Debuggens von systemeigenem C++-Code. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Anwenden von Änderungen beim fortfahren (nur systemeigen)**: Visual Studio automatisch kompiliert und wendet alle ausstehenden codeänderungen, die Sie vorgenommen haben, wenn den Prozess vom Zustand "unterbrochen". Ist diese Option nicht aktiviert, können Sie Änderungen mit der Option **Codeänderungen übernehmen** im Menü **Debuggen** übernehmen.

- **Warnung bei veraltetem Code (nur systemeigen)**: Warnungen über veralteten Code zu erhalten.

**Ausführung bis Klick anzeigen-Schaltfläche im Editor während des Debuggens**: Wenn diese Option ausgewählt ist, die [Ausführung bis Klick](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) Schaltfläche wird während des Debuggens angezeigt.

**Schließen Sie die Konsole automatisch nach Beenden des Debuggings**: teilt Visual Studio am Ende einer Debugsitzung die Konsole schließen.

## <a name="options-available-in-older-versions-of-visual-studio"></a>In früheren Versionen von Visual Studio verfügbaren Optionen

Wenn Sie eine ältere Version von Visual Studio verwenden, können einige zusätzlichen Optionen vorhanden sein.

**Ausnahmen-Assistenten aktivieren**: für verwalteten Code ermöglicht es den Ausnahmen-Assistenten. Ab Visual Studio 2017, ersetzt der Ausnahmen-Hilfe des Ausnahmen-Assistenten.

**Aufrufliste für Ausnahmefehler entladen**: bewirkt, dass die **Aufrufliste** Fenster aus, um ein Rollback die Aufrufliste zu dem Punkt, bevor der Ausnahmefehler aufgetreten ist.

**Warnhinweis anzeigen, wenn keine Symbole beim Starten (nur systemeigen)**: Zeigt eine Warnmeldung angezeigt, wenn Sie ein Programm debuggen, für das der Debugger keine Symbolinformationen hat.

**Warnhinweis anzeigen, wenn Skriptdebugging beim Start deaktiviert ist**: Zeigt eine Warnmeldung angezeigt, wenn der Debugger mit deaktiviertem Skriptdebuggen gestartet wird.

**Verwenden von systemeigenen Kompatibilitätsmodus**: Wenn diese Option ausgewählt ist, verwendet der Debugger den systemeigenen Debugger von Visual Studio 2010 anstelle des neuen nativen Debuggers.

- Verwenden Sie diese Option beim .NET C++-Code Debuggen, da die neuen Debugmodul das Auswerten von .NET C++-Ausdrücken nicht unterstützt. Durch das Aktivieren des systemeigenen Kompatibilitätsmodus werden aber viele Features deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. Z. B. die legacy-Engine verfügt nicht über viele Schnellansichten für integrierte Typen wie `std::string` in Visual Studio 2015-Projekten.   Verwenden Sie Visual Studio 2013-Projekte für optimales debugging in diesen Fällen an.

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.md)
- [Debugger – Featuretour](../debugger/debugger-feature-tour.md)