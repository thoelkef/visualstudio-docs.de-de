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
ms.openlocfilehash: 80fc504752e181ec75da32f2d1da5dcbf902daf7
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037388"
---
# <a name="general-debugging-options"></a>Allgemeine Optionen für das Debuggen

Wählen Sie zum Festlegen von Optionen für Visual Studio-Debugger **Tools** > **Optionen**, und wählen Sie unter **Debuggen** aktivieren oder deaktivieren Sie die Kontrollkästchen neben den  **Allgemeine** Optionen. Sie können mit allen Standardeinstellungen wiederherstellen **Tools** > **Einstellungen importieren und exportieren** > **alle Einstellungen zurücksetzen**. Um eine Teilmenge der Einstellungen zurückzusetzen, speichern Sie die Einstellungen mit den **-Import- und Exportassistenten Einstellungen** vorzunehmende Änderungen, die Sie testen möchten, klicken Sie dann importieren Sie Ihre Einstellungen wurden gespeichert. anschließend.

Sie können festlegen, dass die folgenden **allgemeine** Optionen:

**Vor Löschen aller Haltepunkte fragen**: Erfordert zum Ausführen des Befehls **Alle Haltepunkte löschen** die Bestätigung.

**Alle Prozesse anhalten, wenn ein Prozess anhält**: Hält im Falle einer Unterbrechung alle Prozesse gleichzeitig an, an die der Debugger angefügt ist.

**Bei Anwendungsdomänengrenzen oder verwaltete/native Übergänge überschreitenden Ausnahmen unterbrechen**: Beim Debuggen im verwalteten oder gemischten Modus kann die Common Language Runtime die Ausnahmen auffangen, die die Grenzen zwischen Anwendungsdomänen oder Grenzen zwischen verwaltetem und systemeigenem Code überschreiten, wenn die folgenden Bedingungen erfüllt sind:

1. Wenn in nativem Code verwalteter Code mit COM-Interop aufgerufen wird und im verwalteten Code eine Ausnahme ausgelöst wird. Finden Sie unter [Einführung in COM-Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Wenn verwalteter Code, der in der Anwendungsdomäne 1 ausgeführt wird, verwalteten Code in der Anwendungsdomäne 2 aufruft und der Code in Anwendungsdomäne 2 eine Ausnahme auslöst. Siehe [Programmieren mit Anwendungsdomänen](/dotnet/articles/framework/app-domains/index).

3. Wenn Code eine Funktion mithilfe der Reflektion aufgerufen, und diese Funktion löst eine Ausnahme aus. Finden Sie unter [Reflektion](/dotnet/framework/reflection-and-codedom/reflection).

Unter Umständen 2 und 3 wird die Ausnahme gelegentlich von verwaltetem Code in abgefangen `mscorlib` und nicht von der common Language Runtime. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.

**Debugging auf Adressebene aktivieren**: Aktiviert erweiterte Funktionen für das Debuggen auf Adressebene (das Fenster **Disassembly**, das Fenster **Register** und Adresshaltepunkte).

- **Disassembly anzeigen, wenn die Quelle nicht verfügbar ist**:   Zeigt automatisch die **Disassembly** Fenster beim Debuggen von Code für die die Quelle nicht verfügbar ist.

**Haltepunktfilter aktivieren**: Mit dieser Option können Sie Filter an Haltepunkten festlegen, damit diese nur für bestimmte Prozesse, Threads oder Computer gelten.

**Die neue Ausnahmen-Hilfe verwenden**: Ermöglicht der Ausnahmen-Hilfe, die den Ausnahmen-Assistenten ersetzt. (Ausnahmen-Hilfe ist ab Visual Studio 2017 unterstützt)

> [!NOTE]
> Für verwalteten Code, der diese Option wurde bereits aufgerufen **Ausnahmen-Assistenten aktivieren** .

**Nur eigenen Code aktivieren**: Der Debugger zeigt nur Benutzercode („Mein Code“) an und durchläuft ihn schrittweise, während systemeigener und sonstiger Code, der optimiert ist oder keine Debugsymbole aufweist, ignoriert wird.

- **Warnen, wenn beim Starten kein Benutzercode ausgeführt wird (nur verwaltet)**:   Wenn beim Debuggen am Anfang "Nur mein Code" aktiviert ist, warnt diese Option Sie, wenn kein Benutzercode ("Eigener Code") vorhanden ist.

**Durchlaufen des .NET Framework-Quellcodes aktivieren**: Ermöglicht es dem Debugger, die .NET Framework-Quelle schrittweise auszuführen. Automatisch durch Aktivieren dieser Option wird nur mein Code deaktiviert. .NET Framework-Symbole werden an einen Cachespeicherort heruntergeladen. Ändern des cachespeicherorts mit der **Optionen** Dialogfeld **Debuggen** Kategorie **Symbole** Seite.

**Eigenschaften und Operatoren überspringen (nur verwaltet)**: Verhindert, dass der Debugger Eigenschaften und Operatoren in verwaltetem Code schrittweise ausführt.

**Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**: Aktiviert die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in Variablenfenstern und im Dialogfeld **Schnellüberwachung**.

- **Zeichenfolgenkonvertierungsfunktion für Objekte in Variablenfenstern aufrufen (nur C# und JavaScript)**: Führt einen impliziten Zeichenkonvertierungsaufruf beim Auswerten von Objekten in Variablenfenstern aus. Das Ergebnis wird als eine Zeichenfolge anstatt in der Typname angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann vom DebuggerDisplay-Attribut überschrieben werden (siehe [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)).

**Quellserverunterstützung aktivieren**: Weist den Visual Studio-Debugger an, die Quelldateien aus den Quellservern abzurufen, die das SrcSrv-Protokoll (`srcsrv.dll`) implementieren. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen zum SrcSrv-Setup finden Sie unter den [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) Dokumentation. Darüber hinaus finden Sie unter [angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Da das Lesen von *PDB*-Dateien beliebigen Code in den Dateien ausführen kann, vergewissern Sie sich, dass Sie dem Server vertrauen können.

- **Diagnosemeldungen für Quellserver im Ausgabefenster drucken**:   Wenn die Quellserverunterstützung aktiviert ist, aktiviert diese Einstellung die diagnostische Anzeige.

- **Quellserver für teilweise vertrauenswürdige Assemblys (nur verwaltet) zulassen**:   Wenn die Quellserverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten beim Nichtabrufen von Quellen für teilweise vertrauenswürdige Assemblys.

- **Alle nicht vertrauenswürdigen Quellserverbefehle ohne Aufforderung ausführen**:   Wenn die quellserverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten von eingabeaufforderungen festzulegen, wenn es sich bei einen nicht vertrauenswürdigen Befehl ausführen.

**Quelllinkunterstützung aktivieren**: Weist den Visual Studio-Debugger zum Herunterladen der Quelldateien für *PDB* Dateien, die Informationen der Link "Quelle" enthalten. Weitere Informationen zu den Link "Quelle", finden Sie unter den [quellenspezifikation-Verknüpfung](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
> Da der Link "Quelle" werden Dateien, die über http oder Https heruntergeladen haben, stellen Sie sicher, dass Sie vertrauen den *PDB* Datei.

- **Für alle Quellenlinkanforderungen Fallback auf die Authentifizierung über die Git-Anmeldeinformationsverwaltung durchführen**:   Wenn Unterstützung für Quelllink aktiviert ist und eine Anforderung der Link "Quelle" schlägt die Authentifizierung fehl, ruft Visual Studio klicken Sie dann Git Credential Manager.

**Bei Haltepunkten und aktueller Anweisung (nur C++) die gesamte Zeile markieren**: Wenn der Debugger einen Haltepunkt oder die aktuelle Anweisung hervorhebt, wird die ganze Zeile hervorgehoben.

**Quelldateien müssen exakt mit der Originalversion übereinstimmen**: Fordert den Debugger auf, zu prüfen, ob die Quelldatei mit der Version des Quellcodes übereinstimmt, mit dem die ausführbare Datei erstellt wurde, die Sie debuggen. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert, eine übereinstimmende Quelle zu suchen. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt.

**Gesamten Text aus Ausgabefenster an das Direktfenster umleiten**: Sendet alle Debuggermeldungen, die normalerweise im **Ausgabefenster** angezeigt werden, an das **Direktfenster**.

**Unformatierte Struktur von Objekten in Variablenfenstern anzeigen**: Deaktiviert alle Anpassungen von Objektstrukturansichten. Weitere Informationen zu ansichtsanpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-dot-managed-objects.md).

**JIT-Optimierung beim Laden von Modulen unterdrücken (nur verwaltet)**: Deaktiviert die JIT-Optimierung von verwaltetem Code, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt ist. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird. Weitere Informationen finden Sie unter [JIT-Optimierung und-Debuggen](../debugger/jit-optimization-and-debugging.md).

**Aktivieren Sie JavaScript-debugging für ASP.NET (Chrome, Microsoft Edge und IE)**: Ermöglicht es den Skriptdebugger für ASP.NET-Apps. Bei der ersten Verwendung in Chrome müssen Sie sich in den Browser Chrome-Erweiterungen zu aktivieren, die Sie installiert haben. Deaktivieren Sie diese Option, um zum alten Verhalten zurückzukehren.

**Microsoft Edge-Entwicklertools für UWP-JavaScript-Apps aktivieren (experimentell)**: Ermöglicht die Entwicklertools für UWP-JavaScript-apps in Microsoft Edge.

**Legacy-Chrome-JavaScript-Debugger für ASP.NET aktivieren**: Kann den legacy-Chrome-JavaScript-Skriptdebugger für ASP.NET-Apps. Bei der ersten Verwendung in Chrome müssen Sie sich in den Browser Chrome-Erweiterungen zu aktivieren, die Sie installiert haben.

**Bei der Ausführung von Visual Studio als Administrator experimentelle Möglichkeit zum Starten des Chrome-JavaScript-Debuggens verwenden**: Teilt Visual Studio, um eine neue Methode zum Chrome während der JavaScript-debugging zu starten. versuchen Sie es.

**DLL-Exporte laden (nur native)**: Lädt DLL‑Exporttabellen. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.

Verwenden Sie `dumpbin /exports`, um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](/cpp/build/reference/dash-exports).

**Diagramm mit parallelen Stapeln von unten nach oben anzeigen**: Steuert die Richtung, in der Stapel im Fenster **Parallele Stapel** angezeigt werden.

**Ausnahmen für den GPU-Speicherzugriff ignorieren, wenn der Wert durch die geschriebenen Daten nicht geändert wurde**: Ignoriert Racebedingungen, die während des Debuggens erkannt wurden, wenn sich die Daten nicht geändert haben. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).

**Verwalteten Kompatibilitätsmodus verwenden**: Ersetzt die Standarddebug-Engine durch eine Legacyversion, um die folgenden Szenarien zu ermöglichen:

- Verwenden Sie .NET Framework-Sprache außer C#, Visual Basic oder F# , einen eigenen Expression Evaluator bereitstellt (Dies schließt C++ / CLI).

- Sie möchten bearbeiten und Fortfahren für C++-Projekte beim Debuggen im gemischten Modus aktivieren.

> [!NOTE]
> Auswählen des verwalteten Kompatibilitätsmodus deaktiviert Modus einige Features, die nur im standardmäßigen Debugmodul implementiert werden. Im Visual Studio 2012 wurde die Legacyversion des Debugmoduls ersetzt.

**Die älteren C#- and VB-Ausdrucksauswertungen verwenden**: Der Debugger verwendet Visual Studio 2013 C# oder VB-ausdrucksauswertungen anstelle der Visual Studio 2015 Roslyn-basierten ausdrucksauswertungen.

**Warnen, wenn benutzerdefinierte Debugger für die Anzeige potenziell unsicherer Prozesse verwendet werden (nur verwaltet)**: Visual Studio warnt Sie bei Verwendung einer benutzerdefinierten Debuggerschnellansicht, die im zu debuggenden Prozess Code ausführt, da es sich um unsicheren Code handeln könnte.

**Debugging-Heapzuweisung von Windows verwenden (nur nativ)**: Aktiviert den Debugheap von Windows, um die Heapdiagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.

**UI-Debugtools für XAML aktivieren**: Die Fenster „Visuelle Echtzeitstruktur“ und „Echtzeit-Eigenschaften-Explorer“ werden angezeigt, wenn Sie mit dem Debuggen eines unterstützten Projekttyps beginnen (**F5**). Weitere Informationen finden Sie unter [Überprüfen von XAML-Eigenschaften während des Debuggens](../debugger/inspect-xaml-properties-while-debugging.md).

- **Voransicht für ausgewählte Elemente in der visuellen Echtzeitstruktur anzeigen**:   Das XAML-Element, dessen Kontext ausgewählt ist, ist auch im Fenster **Visuelle Echtzeitstruktur** ausgewählt.

- **Laufzeittools in Anwendung anzeigen**: Zeigt die **Live Visual Tree** Befehle in einer Symbolleiste des Hauptfensters der XAML-Anwendung, die gedebuggt wird. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt.

- **Aktivieren von "Hot" Reload XAML**: Können Sie die XAML-Funktion "Hot" Reload mit XAML-Code verwenden, wenn Ihre app ausgeführt wird. (Diese Funktion wurde bereits aufgerufen "XAML bearbeiten und Fortfahren")

**Diagnosetools beim Debuggen aktivieren**: Das Fenster **Diagnosetools** wird während des Debuggens angezeigt.

**PerfTip für verstrichene Zeit beim Debuggen anzeigen**: Das Codefenster zeigt an, wie viel Zeit bei einem bestimmten Methodenaufruf während des Debuggens verstrichen ist.

**„Bearbeiten und Fortfahren“ aktivieren**: Ermöglicht die bearbeiten und Fortfahren-Funktionalität während des Debuggens.

- **natives Bearbeiten und Fortfahren aktivieren**: Sie können die Funktion „Bearbeiten und Fortfahren“ während des Debuggens von systemeigenem C++-Code verwenden. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Änderungen beim Fortfahren anwenden (nur nativ)**: Beim Fortsetzen eines unterbrochenen Prozesses kompiliert Visual Studio automatisch alle ausstehenden Codeänderungen und wendet sie an. Ist diese Option nicht aktiviert, können Sie Änderungen mit der Option **Codeänderungen übernehmen** im Menü **Debuggen** übernehmen.

- **Warnung bei veraltetem Code (nur nativ)**:   Ruft Warnungen über veralteten Code ab.

**Ausführung bis Klick anzeigen-Schaltfläche im Editor während des Debuggens**: Wenn diese Option ausgewählt ist, die [Ausführung bis Klick](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) Schaltfläche wird während des Debuggens angezeigt.

**Konsole beim Beenden des Debuggings automatisch schließen**: Teilt Visual Studio, um die Konsole schließen, am Ende einer Debugsitzung an.

## <a name="options-available-in-older-versions-of-visual-studio"></a>In früheren Versionen von Visual Studio verfügbaren Optionen

Wenn Sie eine ältere Version von Visual Studio verwenden, können einige zusätzlichen Optionen vorhanden sein.

**Ausnahmen-Assistent aktivieren**: Für verwalteten Code können Ausnahmen-Assistenten. Ab Visual Studio 2017, ersetzt der Ausnahmen-Hilfe des Ausnahmen-Assistenten.

**Aufrufliste für Ausnahmefehler entladen**: Führt dazu, dass das Fenster **Aufrufliste** die Aufrufliste an den Punkt zurücksetzt, bevor der Ausnahmefehler aufgetreten ist.

**Warnung, wenn keine Symbole beim Starten gefunden werden (nur nativ)**: Zeigt eine Warnmeldung angezeigt, wenn Sie ein Programm debuggen, für die der Debugger keine Symbolinformationen hat.

**Warnung, wenn Skriptdebugging beim Start deaktiviert ist**: Zeigt ein Warnungsdialogfeld an, wenn der Debugger mit deaktiviertem Skriptdebuggen gestartet wird.

**nativen Kompatibilitätsmodus verwenden**: Wenn diese Option ausgewählt ist, wird der native Debugger von Visual Studio 2010 anstelle des neuen nativen Debuggers verwendet.

- Verwenden Sie diese Option beim .NET C++-Code Debuggen, da die neuen Debugmodul das Auswerten von .NET C++-Ausdrücken nicht unterstützt. Durch das Aktivieren des systemeigenen Kompatibilitätsmodus werden aber viele Features deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. Z. B. die legacy-Engine verfügt nicht über viele Schnellansichten für integrierte Typen wie `std::string` in Visual Studio 2015-Projekten.   Verwenden Sie Visual Studio 2013-Projekte für optimales debugging in diesen Fällen an.

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
