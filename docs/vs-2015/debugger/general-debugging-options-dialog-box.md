---
title: Allgemein, Debuggen, Dialog Feld "Optionen" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c53af4a8e0f42708ab94d7206a9c0cc54819798
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573553"
---
# <a name="general-debugging-options-dialog-box"></a>Allgemein, Debuggen, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Auf der Seite Extras > Optionen > Debugging >**Allgemein** können Sie die folgenden Optionen festlegen:  
  
 **Vor dem Löschen aller Haltepunkte Fragen**  
 Erfordert zum Ausführen des Befehls **Alle Haltepunkte löschen** die Bestätigung.  
  
 **Alle Prozesse anhalten, wenn ein Prozess unterbrochen wird**  
 Hält im Falle einer Unterbrechung alle Prozesse gleichzeitig an, an die der Debugger angefügt ist.  
  
 **Unterbrechen, wenn Ausnahmen Anwendungs Domänen-oder verwaltete/native Grenzen überschreiten**  
 Beim Debuggen im verwalteten oder gemischten Modus kann die Common Language Runtime die Ausnahmen auffangen, die die Grenzen zwischen Anwendungsdomänen oder Grenzen zwischen verwaltetem und systemeigenem Code überschreiten, wenn die folgenden Bedingungen erfüllt sind:  
  
 1 \), wenn nativer Code verwalteten Code mithilfe von COM-Interop aufruft und der verwaltete Code eine Ausnahme auslöst. Weitere Informationen finden [Sie unter Einführung in COM-Interop](https://msdn.microsoft.com/library/8bd62e68-383d-407f-998b-29aa0ce0fd67).  
  
 2 \), wenn verwalteter Code, der in der Anwendungsdomäne 1 ausgeführt wird, verwalteten Code in der Anwendungsdomäne 2 aufruft und der Code in Anwendungsdomäne 2 eine Ausnahme auslöst. Siehe [Programmieren mit Anwendungs Domänen](https://msdn.microsoft.com/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3 \), wenn Code eine Funktion mithilfe von Reflektion aufruft und die Funktion eine Ausnahme auslöst. Siehe [Reflektion](https://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775).  
  
 In den Fällen 2) und 3) wird die Ausnahme gelegentlich von verwaltetem Code in `mscorlib` und nicht von der Common Language Runtime aufgefangen. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.  
  
 **Debugging auf Adress Ebene aktivieren**  
 Aktiviert erweiterte Funktionen für das Debuggen auf Adressebene (das Fenster **Disassembly**, das Fenster **Register** und Adresshaltepunkte).  
  
 **Disassembly anzeigen, wenn die Quelle nicht verfügbar ist**  
 Das Fenster **Disassembly** wird automatisch angezeigt, wenn Sie versuchen, Code zu debuggen, für den die Quelle nicht verfügbar ist  
  
 **Haltepunkt Filter aktivieren**  
 Ermöglicht es Ihnen, Filter für Haltepunkte festzulegen, sodass Sie nur bestimmte Prozesse, Threads oder Computer betreffen.  
  
 **Aktivieren des Ausnahmen-Assistenten**  
 Nur für verwalteten Code. Verwaltete Ausnahmen öffnen das Dialogfeld des Ausnahmen-Assistenten.  Siehe [Ausnahmen-Assistent](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb).  
  
 **Entladen der aufrufsstapel bei nicht behandelten Ausnahmen**  
 Führt dazu, dass das Fenster **Aufrufliste** die Aufrufliste an den Punkt zurücksetzt, bevor der Ausnahmefehler aufgetreten ist.  
  
 **Nur meinen Code aktivieren**  
 Der Debugger zeigt nur Benutzercode („Mein Code“) an und durchläuft ihn schrittweise, während systemeigener und sonstiger Code, der optimiert ist oder keine Debugsymbole aufweist, ignoriert wird.  
  
 **Alle Member für Nichtbenutzer Objekte in Variablen Fenstern anzeigen (nur Visual Basic)**  
 Aktiviert die Anzeige nicht öffentlicher Member in Objekten in Nichtbenutzercode (nicht "Nur eigener Code").  
  
 **Beim Start warnen, wenn kein Benutzercode**  
 Wenn beim Debuggen am Anfang "Nur mein Code" aktiviert ist, warnt diese Option Sie, wenn kein Benutzercode ("Eigener Code") vorhanden ist.  
  
 **Schrittweise .NET Framework Quelle aktivieren**  
 Ermöglicht es dem Debugger, die .NET Framework-Quelle schrittweise auszuführen. Durch Aktivieren dieser Option wird "Nur mein Code" automatisch deaktiviert. .NET Framework-Symbole werden an einen Cachespeicherort heruntergeladen. Sie können den Cache Speicherort im Dialogfeld **Optionen** , **debugkategorie** , **Symbol** Seite ändern.  
  
 **Eigenschaften und Operatoren überspringen (nur verwaltet)**  
 Verhindert, dass der Debugger Eigenschaften und Operatoren in verwaltetem Code schrittweise ausführt.  
  
 **Eigenschaften Auswertung und andere implizite Funktionsaufrufe aktivieren**  
 Aktiviert die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in Variablenfenstern und im Dialogfeld **Schnellüberwachung**.  
  
 **Zeichen folgen Konvertierungs Funktion für Objekte in Variablen FensternC# (nur JavaScript)**  
 Führt einen impliziten Zeichenkonvertierungsaufruf beim Auswerten von Objekten in Variablenfenstern aus. Deshalb wird dieses Ergebnis nicht als Typname, sondern als Zeichenfolge angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann durch das Attribut "tbuggerdisplay" überschrieben werden (siehe [Verwenden des Attributs](../debugger/using-the-debuggerdisplay-attribute.md)"Debug-Display").  
  
 **Quellserverunterstützung aktivieren**  
 Weist den Visual Studio-Debugger an, die Quelldateien aus den Quellservern abzurufen, die das SrcSrv-Protokoll (`srcsrv.dll`) implementieren. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen zum SrcSrv-Setup finden Sie in der Dokumentation zu den Debugtools für Windows. Weitere Informationen finden Sie unter [Angeben von Symbol-(PDB-) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Da das Lesen von PDB-Dateien beliebigen Code in den Dateien ausführen kann, vergewissern Sie sich, dass Sie dem Server vertrauen können.  
  
 **Diagnosemeldungen des Quell Servers im Ausgabefenster drucken**  
 Wenn die Quellserverunterstützung aktiviert ist, aktiviert diese Einstellung die diagnostische Anzeige.  
  
 **Quell Server für teilweise vertrauenswürdige Assemblys zulassen (nur verwaltet)**  
 Wenn die Quellserverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten beim Nichtabrufen von Quellen für teilweise vertrauenswürdige Assemblys.  
  
 **Gesamte Zeile für Breakpoints und Current-Anweisung markieren**  
 Wenn der Debugger einen Haltepunkt oder die aktuelle Anweisung hervorhebt, wird die ganze Zeile hervorgehoben.  
  
 **Quelldateien müssen exakt mit der Originalversion übereinstimmen**  
 Fordert den Debugger auf, zu prüfen, ob die Quelldatei mit der Version des Quellcodes übereinstimmt, mit dem die ausführbare Datei erstellt wurde, die Sie debuggen. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert, eine übereinstimmende Quelle zu suchen. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt.  
  
 **Gesamten Text des Ausgabe Fensters an das direkt Fenster umleiten**  
 Sendet alle Debuggermeldungen, die normalerweise im **Ausgabefenster** angezeigt werden, an das **Direktfenster**.  
  
 **Rohstruktur von Objekten in Variablen Fenstern anzeigen**  
 Deaktiviert alle Anpassungen von Objektstrukturansichten. Weitere Informationen zu Ansichts Anpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-managed-objects.md).  
  
 **JIT-Optimierung beim Laden von Modulen unterdrücken (nur verwaltet)**  
 Deaktiviert die JIT-Optimierung von verwaltetem Code, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt ist. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird.  
  
 **Warnen, wenn keine Symbole beim Starten (nur nativ)**  
 Zeigt eine Warnungsdialogfeld an, wenn Sie ein Programm debuggen, für das der Debugger keine Symbolinformationen hat.  
  
 **Warnung, wenn Skript Debugging beim Start deaktiviert ist**  
 Zeigt ein Warnungsdialogfeld an, wenn der Debugger mit deaktiviertem Skriptdebuggen gestartet wird.  
  
 **DLL-Exporte laden**  
 Lädt DLL‑Exporttabellen. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.  
  
 Verwenden Sie `dumpbin /exports`, um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen finden Sie unter [Dump bin/Exports](https://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
 **Diagramm der parallelen Stapel unten nach oben anzeigen**  
 Steuert die Richtung, in der Stapel im Fenster **Parallele Stapel** angezeigt werden.  
  
 **Ausnahmen für den GPU-Speicherzugriff ignorieren, wenn der Wert durch die geschriebenen Daten nicht geändert wurde**  
 Ignoriert Racebedingungen, die während des Debuggens erkannt wurden, wenn sich die Daten nicht geändert haben. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).  
  
 **Verwalteten Kompatibilitätsmodus verwenden**  
 Ersetzt die Standarddebug-Engine durch eine Legacyversion, um die folgenden Szenarien zu ermöglichen:  
  
- Sie verwenden eine andere .NET Framework-Sprache als C#, VB oder F#, die einen eigenen Expression Evaluator bereitstellt (dies schließt C++/CLI mit ein).  
  
- Sie möchten „Bearbeiten und Fortfahren“ für C++-Projekte beim Debuggen im gemischten Modus aktivieren.  
  
  Beachten Sie, dass durch Auswählen des verwalteten Kompatibilitätsmodus einige Funktionen deaktiviert werden, die nur in der standardmäßigen Debug-Engine implementiert werden.  
  
  **Systemeigenen Kompatibilitätsmodus verwenden**  
  Wenn diese Option ausgewählt ist, wird der native Debugger von Visual Studio 2010 anstelle des neuen nativen Debuggers verwendet.  
  
  Beim Debuggen von .NET C++-Code sollten Sie diese Option verwenden, da die neue Debug-Engine das Auswerten von .NET C++-Ausdrücken nicht unterstützt. Durch das Aktivieren des systemeigenen Kompatibilitätsmodus werden aber viele Features deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. Beispielsweise fehlen in der Legacy-Engine viele Visualisierungen für integrierte Typen wie `std::string` in Visual Studio 2015-Projekten.  Verwenden Sie Visual Studio 2013-Projekte für die optimale debuggingdarstellung in diesen Fällen.  
  
  **Verwenden der Legacy C# -und VB-Ausdrucks Auswertung**  
  Der Debugger verwendet anstelle der Visual Studio 2015 Roslyn-basierten Ausdrucksauswertungen die Visual Studio 2013 C#/VB-Ausdrucksauswertungen.  
  
  **Warnen, wenn benutzerdefinierte Debugger-Visualisierungen für potenziell unsichere Prozesse verwendet werden (nur verwaltet)**  
  Visual Studio warnt Sie bei Verwendung einer benutzerdefinierten Debuggerschnellansicht, die im zu debuggenden Prozess Code ausführt, da es sich um unsicheren Code handeln könnte.  
  
  **Windows-Debug-Heap Zuweisung aktivieren (nur System eigen)**  
  Aktiviert den Debugheap von Windows, um die Heapdiagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.  
  
  **UI-Debuggingtools für XAML aktivieren**  
  Die Fenster „Visuelle Live-Struktur“ und „Echtzeit-Eigenschaften-Explorer“ werden angezeigt, wenn Sie mit dem Debuggen eines unterstützten Projekttyps beginnen (F5). Weitere Informationen finden Sie unter über [Prüfen von XAML-Eigenschaften beim Debuggen](../debugger/inspect-xaml-properties-while-debugging.md).  
  
  **Vorschau der ausgewählten Elemente in der visuellen Live Struktur anzeigen**  
  Das XAML-Element, dessen Kontext ausgewählt ist, ist auch im Fenster **Visuelle Echtzeitstruktur** ausgewählt.  
  
  **Lauf Zeit Tools in Anwendung anzeigen**  
  Zeigt die Befehle der **visuellen Live** Struktur in einer Symbolleiste im Hauptfenster der XAML-Anwendung an, die gedebuggt wird. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt.  
  
  **Diagnosetools während des Debuggens aktivieren**  
  Das Fenster **Diagnosetools** wird während des Debuggens angezeigt. Weitere Informationen finden Sie unter [debuggerintegrierte Profilerstellung](/visualstudio/profiling/running-profiling-tools-with-or-without-the-debugger).  
  
  **Perftip für verstrichene Zeit beim Debuggen anzeigen**  
  Das Codefenster zeigt an, wie viel Zeit bei einem bestimmten Methodenaufruf während des Debuggens verstrichen ist.  
  
  **"Bearbeiten und Fortfahren" aktivieren**  
  Sie können die Funktion „Bearbeiten und Fortfahren“ während des Debuggens verwenden.  
  
  **System eigenes bearbeiten und Fortfahren aktivieren**  
  Sie können die Funktion „Bearbeiten und Fortfahren“ während des Debuggens von systemeigenem C++-Code verwenden. Weitere Informationen finden Sie unter " [Bearbeiten und Fortfahren C++" (Visual)](../debugger/edit-and-continue-visual-cpp.md).  
  
  **Änderungen beim Fortfahren anwenden (nur nativ)**  
  Beim Fortsetzen eines unterbrochenen Prozesses kompiliert Visual Studio automatisch alle ausstehenden Codeänderungen und wendet sie an. Ist diese Option nicht aktiviert, können Sie Änderungen mit der Option „Codeänderungen übernehmen“ im Menü „Debuggen“ übernehmen.  
  
  **Warnung bei veraltetem Code (nur nativ)**  
  Ruft Warnungen über veralteten Code ab.  
  
  **Vorkompilierung zulassen (nur nativ)**  
  Vorkompilieren ist zulässig.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)
