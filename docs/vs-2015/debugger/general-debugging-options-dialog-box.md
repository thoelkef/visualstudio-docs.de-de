---
title: Allgemein, Debuggen, Dialogfeld "Optionen" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dab045b147b4ce929106c26befcae58c80b99239
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854324"
---
# <a name="general-debugging-options-dialog-box"></a>Allgemein, Debuggen, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die**Extras / Optionen / Debugging / Allgemein** auf Seite können Sie die folgenden Optionen festlegen:  
  
 **Vor dem Löschen aller Haltepunkte Fragen**  
 Erfordert eine Bestätigung vor dem Abschluss der **alle Haltepunkte löschen** Befehl.  
  
 **Anhalten Sie alle Prozesse, wenn ein Prozess anhält**  
 Hält im Falle einer Unterbrechung alle Prozesse gleichzeitig an, an die der Debugger angefügt ist.  
  
 **Unterbrechen Sie Ausnahmen oder verwaltete/systemeigene Übergänge überschreitenden**  
 Beim Debuggen im verwalteten oder gemischten Modus kann die Common Language Runtime die Ausnahmen auffangen, die die Grenzen zwischen Anwendungsdomänen oder Grenzen zwischen verwaltetem und systemeigenem Code überschreiten, wenn die folgenden Bedingungen erfüllt sind:  
  
 1\) bei nativem Code verwalteter Code mit COM-Interop aufgerufen und der verwaltete Code löst eine Ausnahme aus. Finden Sie unter [Einführung in COM-Interop](http://msdn.microsoft.com/library/8bd62e68-383d-407f-998b-29aa0ce0fd67).  
  
 2\) bei verwaltetem Code in Anwendungsdomäne 1 ausgeführt wird verwalteter Code in Anwendungsdomäne 2 aufgerufen und der Code in Anwendungsdomäne 2 eine Ausnahme ausgelöst. Finden Sie unter [Programmieren mit Anwendungsdomänen](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3\) Wenn Code eine Funktion mithilfe der Reflektion aufgerufen und die Funktion löst eine Ausnahme aus. Finden Sie unter [Reflektion](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775).  
  
 In den Fällen 2) und 3) wird die Ausnahme gelegentlich von verwaltetem Code in `mscorlib` und nicht von der Common Language Runtime aufgefangen. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.  
  
 **Debuggen auf Adressebene aktivieren**  
 Aktiviert erweiterte Funktionen für das Debuggen auf Adressebene (das **Disassembly** Fenster die **registriert** Fenster und Adresshaltepunkte).  
  
 **Zeigen Sie Disassemblierung an, wenn die Quelle nicht verfügbar ist**  
 Zeigt automatisch die **Disassembly** Fenster, wenn Sie versuchen, den Code für die Quellcode zu Debuggen ist nicht verfügbar.  
  
 **Haltepunktfilter aktivieren**  
 Mit dieser Option können Sie Filter an Haltepunkten festlegen, damit diese nur für bestimmte Prozesse, Threads oder Computer gelten.  
  
 **Ausnahmen-Assistenten aktivieren**  
 Nur für verwalteten Code. Verwaltete Ausnahmen öffnen das Dialogfeld des Ausnahmen-Assistenten.  Finden Sie unter [Ausnahmen-Assistent](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb).  
  
 **Aufrufliste für Ausnahmefehler entladen**  
 Bewirkt, dass die **Aufrufliste** Fenster aus, um ein Rollback die Aufrufliste zu dem Punkt, bevor der Ausnahmefehler aufgetreten ist.  
  
 **Nur meinen Code aktivieren**  
 Der Debugger zeigt nur Benutzercode („Mein Code“) an und durchläuft ihn schrittweise, während systemeigener und sonstiger Code, der optimiert ist oder keine Debugsymbole aufweist, ignoriert wird.  
  
 **Zeigen Sie alle Member für Nichtbenutzerobjekte in Variablenfenstern (nur Visual Basic)**  
 Aktiviert die Anzeige nicht öffentlicher Member in Objekten in Nichtbenutzercode (nicht "Nur eigener Code").  
  
 **Warnhinweis anzeigen Sie, wenn kein Benutzercode beim Start**  
 Wenn beim Debuggen am Anfang "Nur mein Code" aktiviert ist, warnt diese Option Sie, wenn kein Benutzercode ("Eigener Code") vorhanden ist.  
  
 **Aktivieren von .NET Framework-Quellcodes**  
 Ermöglicht es dem Debugger, die .NET Framework-Quelle schrittweise auszuführen. Durch Aktivieren dieser Option wird "Nur mein Code" automatisch deaktiviert. .NET Framework-Symbole werden an einen Cachespeicherort heruntergeladen. Sie können den Cachespeicherort im Ändern der **Optionen** Dialogfeld **Debuggen** Kategorie **Symbole** Seite.  
  
 **Eigenschaften und Operatoren überspringen (nur verwaltet)**  
 Verhindert, dass der Debugger Eigenschaften und Operatoren in verwaltetem Code schrittweise ausführt.  
  
 **Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**  
 Aktiviert die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in Variablenfenstern und **Schnellüberwachung** Dialogfeld.  
  
 **Zeichenfolgenkonvertierungsfunktion für Objekte in Variablenfenstern (C#- und JavaScript nur) aufrufen.**  
 Führt einen impliziten Zeichenkonvertierungsaufruf beim Auswerten von Objekten in Variablenfenstern aus. Deshalb wird dieses Ergebnis nicht als Typname, sondern als Zeichenfolge angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann vom DebuggerDisplay-Attribut überschrieben werden (siehe [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
 **Quellserverunterstützung aktivieren**  
 Weist den Visual Studio-Debugger an, die Quelldateien aus den Quellservern abzurufen, die das SrcSrv-Protokoll (`srcsrv.dll`) implementieren. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen zum SrcSrv-Setup finden Sie in der Dokumentation zu den Debugtools für Windows. Darüber hinaus finden Sie unter [angeben von Symbol (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Da das Lesen von PDB-Dateien beliebigen Code in den Dateien ausführen kann, vergewissern Sie sich, dass Sie dem Server vertrauen können.  
  
 **Drucken Sie Source Server-diagnosemeldungen im Ausgabefenster**  
 Wenn die Quellserverunterstützung aktiviert ist, aktiviert diese Einstellung die diagnostische Anzeige.  
  
 **Quellserver für teilweise vertrauenswürdige Assemblys (nur verwaltet) zulassen**  
 Wenn die Quellserverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten beim Nichtabrufen von Quellen für teilweise vertrauenswürdige Assemblys.  
  
 **Bei Haltepunkten und aktueller Anweisung gesamte Zeile markieren**  
 Wenn der Debugger einen Haltepunkt oder die aktuelle Anweisung hervorhebt, wird die ganze Zeile hervorgehoben.  
  
 **Quelldateien Sie müssen exakt mit Originalversion übereinstimmen**  
 Fordert den Debugger auf, zu prüfen, ob die Quelldatei mit der Version des Quellcodes übereinstimmt, mit dem die ausführbare Datei erstellt wurde, die Sie debuggen. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert, eine übereinstimmende Quelle zu suchen. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt.  
  
 **Umleiten Sie gesamten Text aus Ausgabefenster an das Direktfenster**  
 Sendet alle Debuggermeldungen, die normalerweise in der **Ausgabe** Fenster aus, um die **direkt** Fenster stattdessen.  
  
 **Unformatierte Struktur von Objekten in Variablenfenstern anzeigen**  
 Deaktiviert alle Anpassungen von Objektstrukturansichten. Weitere Informationen zu ansichtsanpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
 **Unterdrücken der JIT-Optimierung beim Laden von Modulen (nur verwaltet)**  
 Deaktiviert die JIT-Optimierung von verwaltetem Code, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt ist. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird.  
  
 **Warnhinweis anzeigen Sie, wenn keine Symbole beim Starten (nur systemeigen)**  
 Zeigt eine Warnungsdialogfeld an, wenn Sie ein Programm debuggen, für das der Debugger keine Symbolinformationen hat.  
  
 **Warnhinweis anzeigen Sie, wenn Skriptdebugging beim Start deaktiviert ist**  
 Zeigt ein Warnungsdialogfeld an, wenn der Debugger mit deaktiviertem Skriptdebuggen gestartet wird.  
  
 **DLL‑Exporte laden**  
 Lädt DLL‑Exporttabellen. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.  
  
 Verwenden Sie `dumpbin /exports`, um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](http://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
 **Parallele Stapel Diagramm unten nach oben anzeigen**  
 Steuert die Richtung, in der Stapel, in angezeigt werden, der **parallele Stapel** Fenster.  
  
 **Ignorieren Sie GPU Ausnahmen Speicherzugriff, wenn die geschriebenen Daten nicht geändert haben**  
 Ignoriert Racebedingungen, die während des Debuggens erkannt wurden, wenn sich die Daten nicht geändert haben. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).  
  
 **Verwalteten Kompatibilitätsmodus verwenden**  
 Ersetzt die Standarddebug-Engine durch eine Legacyversion, um die folgenden Szenarien zu ermöglichen:  
  
- Sie verwenden eine andere .NET Framework-Sprache als C#, VB oder F#, die einen eigenen Expression Evaluator bereitstellt (dies schließt C++/CLI mit ein).  
  
- Sie möchten „Bearbeiten und Fortfahren“ für C++-Projekte beim Debuggen im gemischten Modus aktivieren.  
  
  Beachten Sie, dass durch Auswählen des verwalteten Kompatibilitätsmodus einige Funktionen deaktiviert werden, die nur in der standardmäßigen Debug-Engine implementiert werden.  
  
  **Systemeigenen Kompatibilitätsmodus verwenden**  
  Wenn diese Option ausgewählt ist, wird der native Debugger von Visual Studio 2010 anstelle des neuen nativen Debuggers verwendet.  
  
  Beim Debuggen von .NET C++-Code sollten Sie diese Option verwenden, da die neue Debug-Engine das Auswerten von .NET C++-Ausdrücken nicht unterstützt. Durch das Aktivieren des nativen Kompatibilitätsmodus werden aber viele Funktionen deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. Z. B. die legacy-Engine verfügt nicht über viele Schnellansichten für integrierte Typen wie `std::string` in Visual Studio 2015-Projekten.   Verwenden Sie für ein optimales Debugging in diesen Fällen Visual Studio 2013-Projekte.  
  
  **Verwenden Sie die älteren c# und VB-ausdrucksauswertungen**  
  Der Debugger verwendet anstelle der Visual Studio 2015 Roslyn-basierten Ausdrucksauswertungen die Visual Studio 2013 C#/VB-Ausdrucksauswertungen.  
  
  **Warnen Sie, wenn benutzerdefinierte Debugger für die Anzeige potenziell unsicherer Prozesse (nur verwaltet) verwenden.**  
  Visual Studio warnt Sie bei Verwendung einer benutzerdefinierten Debuggerschnellansicht, die im zu debuggenden Prozess Code ausführt, da es sich um unsicheren Code handeln könnte.  
  
  **Heapzuweisung von Windows Debug (nur systemeigen)**  
  Aktiviert den Debugheap von Windows, um die Heapdiagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.  
  
  **Aktivieren Sie UI-Debuggingtools für XAML**  
  Die Fenster „Visuelle Echtzeitstruktur“ und „Echtzeit-Eigenschaften-Explorer“ werden angezeigt, wenn Sie mit dem Debuggen eines unterstützten Projekttyps beginnen (F5). Weitere Informationen finden Sie unter [Überprüfen von XAML-Eigenschaften während des Debuggens](../debugger/inspect-xaml-properties-while-debugging.md).  
  
  **Vorschau der ausgewählten Elemente in visuelle Echtzeitstruktur**  
  Das XAML-Element, dessen Kontext ausgewählt ist, ebenfalls ausgewählt ist, der **Live Visual Tree** Fenster.  
  
  **Laufzeittools in Anwendung**  
  Zeigt die **Live Visual Tree** Befehle in einer Symbolleiste des Hauptfensters der XAML-Anwendung, die gedebuggt wird. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt.  
  
  **Diagnosetools beim Debuggen aktivieren**  
  Die **Diagnosetools** Fenster wird angezeigt, während des Debuggens. Weitere Informationen finden Sie unter [profilerstellung im Debugger integrierten](http://msdn.microsoft.com/library/a1f40370-7b61-42c2-afc4-0e13eba98859).  
  
  **PerfTip für verstrichene Zeit beim Debuggen anzeigen**  
  Das Codefenster zeigt an, wie viel Zeit bei einem bestimmten Methodenaufruf während des Debuggens verstrichen ist.  
  
  **Bearbeiten und Fortfahren aktivieren**  
  Sie können die Funktion „Bearbeiten und Fortfahren“ während des Debuggens verwenden.  
  
  **Aktivieren Sie systemeigene bearbeiten und fortfahren**  
  Sie können die Funktion „Bearbeiten und Fortfahren“ während des Debuggens von systemeigenem C++-Code verwenden. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
  **Anwenden von Änderungen beim fortfahren (nur systemeigen)**  
  Beim Fortsetzen eines unterbrochenen Prozesses kompiliert Visual Studio automatisch alle ausstehenden Codeänderungen und wendet sie an. Ist diese Option nicht aktiviert, können Sie Änderungen mit der Option „Codeänderungen übernehmen“ im Menü „Debuggen“ übernehmen.  
  
  **Warnung bei veraltetem Code (nur systemeigen)**  
  Ruft Warnungen über veralteten Code ab.  
  
  **Zulassen Sie (nur systemeigen) Vorkompilierung**  
  Vorkompilieren ist zulässig.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)



