---
title: Allgemein, Debuggen, Dialogfeld "Optionen" | Microsoft-Dokumentation
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
ms.openlocfilehash: e46301c84b1a9b27eed8cb6667b312ff73af2960
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280636"
---
# <a name="general-debugging-options-dialog-box"></a>Allgemein, Debuggen, Dialogfeld "Optionen"
Die **Tools > Optionen > Debugging > Allgemein** Seite ermöglicht Ihnen das in diesem Artikel beschriebenen Optionen festlegen.

Wenn Sie die Standardeinstellungen wiederherstellen möchten, erreichen Sie, dass die Verwendung **Tools** > **Einstellungen importieren und exportieren** > **alle Einstellungen zurücksetzen**. Wenn Sie nur eine Teilmenge der Einstellungen zurücksetzen möchten, speichern Sie die Einstellungen in der **-Import- und Exportassistenten Einstellungen** vorzunehmende Änderungen, die Sie testen möchten, klicken Sie dann die gespeicherten Einstellungen später importieren.
  
**Vor dem Löschen aller Haltepunkte Fragen** erfordert eine Bestätigung vor dem Abschluss der **alle Haltepunkte löschen** Befehl.  
  
**Alle Prozesse anhalten, wenn ein Prozess anhält** gleichzeitig unterbricht alle Prozesse, die auf die der Debugger wird, angefügt, wenn eine Unterbrechung auftritt.  
  
**Ausnahmen unterbrechen oder verwaltete/systemeigene Übergänge überschreitenden** In verwalteten oder gemischten Modus zu debuggen, die common Language Runtime kann Ausnahmen abfangen, die Grenzen von Anwendungsdomänen hinweg bei Anwendungsdomänengrenzen verwaltete/systemeigene Übergänge oder beim folgenden Bedingungen sind erfüllt:  
  
1\) bei nativem Code verwalteter Code mit COM-Interop aufgerufen und der verwaltete Code löst eine Ausnahme aus. Finden Sie unter [Einführung in COM-Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) bei verwaltetem Code in Anwendungsdomäne 1 ausgeführt wird verwalteter Code in Anwendungsdomäne 2 aufgerufen und der Code in Anwendungsdomäne 2 eine Ausnahme ausgelöst. Finden Sie unter [Programmieren mit Anwendungsdomänen](/dotnet/articles/framework/app-domains/index).  

3\) Wenn Code eine Funktion mithilfe der Reflektion aufgerufen und die Funktion löst eine Ausnahme aus. Finden Sie unter [Reflektion](/dotnet/framework/reflection-and-codedom/reflection).  
  
In der Bedingung 2 und 3, wird die Ausnahme gelegentlich von verwaltetem Code in abgefangen `mscorlib` anstelle der common Language Runtime. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.  
  
**Debuggen auf Adressebene aktivieren** aktiviert erweiterte Funktionen für das Debuggen auf Adressebene (das **Disassembly** Fenster die **registriert** Fenster und Adresshaltepunkte).  
  
- **Disassemblierung anzeigen, wenn die Quelle nicht verfügbar ist** zeigt automatisch die **Disassembly** Fenster, wenn Sie versuchen, den Code für die Quellcode zu Debuggen ist nicht verfügbar.  
  
**Haltepunktfilter aktivieren** können Sie Filter an Haltepunkten festlegen, sodass sie nur bestimmte Prozesse, Threads oder Computer gelten.  
 
**Verwenden Sie das neue Ausnahmehilfsprogramm** können Sie die Ausnahmen-Hilfe (Visual Studio 2017), die den Ausnahmen-Assistenten ersetzt.
  
> [!NOTE]
> Für verwalteten Code, der diese Option wurde bereits aufgerufen **Ausnahmen-Assistenten aktivieren** . 
  
**Nur eigenen Code aktivieren** der Debugger zeigt und die Schritte in Benutzercode ("Mein Code"), wird ignoriert, und anderen Code, der optimiert ist oder, die keine Debugsymbole.

- **Warnhinweis anzeigen, wenn kein Benutzercode beim Start (nur verwaltet)** beim Starten des Debuggens mit nur mein Code aktiviert, diese Option warnt Sie, wenn kein Benutzercode ("Mein Code") vorhanden ist. 

**Aktivieren von .NET Framework-Quellcodes** ermöglicht es dem Debugger mit Einzelschritten, .NET Framework-Quelle. Durch Aktivieren dieser Option wird "Nur mein Code" automatisch deaktiviert. .NET Framework-Symbole werden an einen Cachespeicherort heruntergeladen. Sie können den Cachespeicherort im Ändern der **Optionen** Dialogfeld **Debuggen** Kategorie **Symbole** Seite.  
  
**Prozedurschritt für Eigenschaften und Operatoren überspringen (nur verwaltet)** verhindert, dass den Debugger Eigenschaften und Operatoren in verwaltetem Code schrittweise.  
  
**Eigenschaftenauswertung und andere implizite Funktionsaufrufe** aktiviert die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in Variablenfenstern und **Schnellüberwachung** Dialogfeld.  
  
- **Zeichenfolgenkonvertierungsfunktion für Objekte in Variablenfenstern (C#- und JavaScript nur) aufrufen** führt Sie einen impliziten Zeichenkonvertierungsaufruf beim Auswerten von Objekten in Variablenfenstern. Das Ergebnis wird als eine Zeichenfolge anstatt in der Typname angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann vom DebuggerDisplay-Attribut überschrieben werden (siehe [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Quellserverunterstützung aktivieren** weist den Visual Studio-Debugger an Quelldateien von Quellservern abzurufen, die das SrcSrv implementieren (`srcsrv.dll`) Protokoll. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen zum SrcSrv-Setup finden Sie unter den [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) Dokumentation. Darüber hinaus finden Sie unter [angeben von Symbol (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Da beim Lesen der *PDB* Dateien beliebigen Code auszuführen, in den Dateien, stellen Sie sicher, dass Sie auf den Server vertrauen können.  
  
- **Source Server-diagnosemeldungen im Ausgabefenster Drucken** Wenn die quellserverunterstützung aktiviert ist, aktiviert diese Einstellung die diagnostische Anzeige.  
  
- **Quellserver für teilweise vertrauenswürdige Assemblys (nur verwaltet) zulassen** Wenn die quellserverunterstützung aktiviert ist, wird diese Einstellung überschreibt das Standardverhalten beim Nichtabrufen von Quellen für teilweise vertrauenswürdige Assemblys.  

**Quelllinkunterstützung aktivieren** weist den Visual Studio-Debugger an Quelldateien für die PDB-Dateien herunterladen, die Informationen der Link "Quelle" enthalten. Weitere Informationen zu den Link "Quelle", finden Sie unter den [Quellenspezifikation-Verknüpfung](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Because Source Link will download files using http or https, make sure you trust the .pdb file.  
  
**Bei Haltepunkten und aktueller Anweisung (nur C++) die gesamte Zeile markieren** , wenn der Debugger einen Haltepunkt oder die aktuelle Anweisung hervorhebt, werden die gesamte Zeile hervorgehoben.  
  
**Quelldateien müssen genau mit übereinstimmen, die ursprüngliche Version** weist den Debugger, um sicherzustellen, dass eine Quelldatei mit der Version des Quellcodes verwendet, um die ausführbare Datei zu erstellen, Sie Debuggen, übereinstimmt. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert werden, um eine übereinstimmende Quelle zu suchen. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt. 
  
**Gesamten Text aus Ausgabefenster an das Direktfenster umleiten** sendet alle Debuggermeldungen, die normalerweise in der **Ausgabe** Fenster aus, um die **direkt** Fenster stattdessen.  
  
**Unformatierte Struktur von Objekten in Variablenfenstern anzeigen** deaktiviert alle objektstrukturansichten. Weitere Informationen zu ansichtsanpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**JIT-Optimierung beim Laden von Modulen (nur verwaltet) unterdrücken** deaktiviert die JIT-Optimierung von verwaltetem Code aus, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt ist. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird. Weitere Informationen finden Sie unter [JIT-Optimierung und Debugging](../debugger/jit-optimization-and-debugging.md).

**Aktivieren Sie JavaScript-debugging für ASP.NET (Chrome und IE)** ermöglicht es den Skriptdebugger für ASP.NET-Apps. Bei der ersten Verwendung in Chrome müssen Sie sich in den Browser, bei der ersten Verwendung zum Aktivieren von Chrome-Erweiterungen, die Sie installiert haben. Deaktivieren Sie diese Option, um zum alten Verhalten zurückzukehren.    

**DLL‑Exporte laden** Dll-Exporttabellen lädt. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.  
  
Um anzuzeigen, welche Symbole in der Exporttabelle einer DLL verfügbar sind, verwenden Sie `dumpbin /exports`. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
**Show parallelen Stapeln von unten nach oben im Diagramm** steuert die Richtung, in der Stapel, in angezeigt werden, der **parallele Stapel** Fenster.
  
**GPU Ausnahmen Speicherzugriff ignorieren, wenn die geschriebenen Daten nicht geändert haben** ignoriert Racebedingungen, die erkannt wurden, während des Debuggens, wenn die Daten nicht geändert haben. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).  
  
**Verwenden verwalteter Kompatibilitätsmodus** ersetzt das standarddebugmodul durch eine Legacyversion, um diese Szenarien zu ermöglichen:  
  
- Sie verwenden eine andere .NET Framework-Sprache als C#, VB oder F#, die einen eigenen Expression Evaluator bereitstellt (dies schließt C++/CLI mit ein).  
  
- Sie möchten „Bearbeiten und Fortfahren“ für C++-Projekte beim Debuggen im gemischten Modus aktivieren.  
  
> [!NOTE]
> Auswählen des verwalteten Kompatibilitätsmodus deaktiviert Modus einige Features, die nur im standardmäßigen Debugmodul implementiert werden. 

**Verwenden Sie die älteren c# und VB-ausdrucksauswertungen** der Debugger wird anstelle der Visual Studio 2015 Roslyn-basierten ausdrucksauswertungen die Visual Studio 2013 C#/VB-ausdrucksauswertungen verwenden.    
  
**Warnen, wenn benutzerdefinierte Debugger für die Anzeige potenziell unsicherer Prozesse (nur verwaltet) mit** Visual Studio warnt Sie bei Verwendung eine benutzerdefinierten Debuggerschnellansicht, die in der zu debuggenden Prozess Code ausgeführt wird, da er nicht sicher ausgeführt werden konnte Code.  
  
**Heapzuweisung von Windows Debug (nur systemeigen)** ermöglicht den Windows-Debugheap, um die heapdiagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.  
  
**Aktivieren von UI-Debuggingtools für XAML** der Live Visual Tree und die Live-Eigenschaften-Explorer-Fenster werden angezeigt, wenn Sie das Debuggen starten (F5) eines unterstützten Projekttyps. Weitere Informationen finden Sie unter [Überprüfen von XAML-Eigenschaften während des Debuggens](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Vorschau der ausgewählten Elemente in visuelle Echtzeitstruktur** der XAML-Element, dessen Kontext ausgewählt ist, ebenfalls ausgewählt ist, der **Live Visual Tree** Fenster.  
  
- **Laufzeittools in Anwendung** zeigt die **Live Visual Tree** Befehle in einer Symbolleiste des Hauptfensters der XAML-Anwendung, die gedebuggt wird. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt. 

- **XAML bearbeiten und Fortfahren aktivieren** können Sie verwenden, bearbeiten und Fortfahren-Funktion für XAML-Code. 
  
**Aktivieren der Diagnosetools während des Debuggens** der **Diagnosetools** Fenster wird angezeigt, während des Debuggens.
  
**PerfTip für verstrichene Zeit beim Debuggen anzeigen** das Codefenster zeigt der verstrichenen Zeit für einen bestimmten Methodenaufruf während des Debuggens.  
  
**Bearbeiten und Fortfahren aktivieren** Sie verwenden, bearbeiten und fortfahren, Funktionen während des Debuggens.  
  
- **Bearbeiten und Fortfahren aktivieren** Sie verwenden, bearbeiten und fortfahren, Funktionen während des Debuggens von systemeigenem C++-Code. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Anwenden von Änderungen beim fortfahren (nur systemeigen)** Visual Studio automatisch kompiliert und wendet alle ausstehenden codeänderungen, die Sie vorgenommen haben, wenn den Prozess vom Zustand "unterbrochen". Wenn nicht ausgewählt ist, können Sie auswählen, um mithilfe des Elements "Codeänderungen übernehmen", unter dem Debugmenü den Ausnahmebefehl Änderungen zu übernehmen.  
  
- **Warnung bei veraltetem Code (nur systemeigen)** Warnungen über veralteten Code zu erhalten.    

**Zeigen Sie auf der Schaltfläche im Editor während des Debuggens ausführen** , wenn diese Option ausgewählt ist, die [Ausführung bis Klick](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) Schaltfläche wird während des Debuggens angezeigt.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>In früheren Versionen von Visual Studio unterstützten Optionen

Wenn Sie eine ältere Version von Visual Studio verwenden, können einige zusätzlichen Optionen vorhanden sein.

**Ausnahmen-Assistenten aktivieren** für verwalteten Code aktiviert des Ausnahmen-Assistenten. In Visual Studio 2017 ersetzt der Ausnahmen-Hilfe des Ausnahmen-Assistenten.

**Aufrufliste für Ausnahmefehler entladen** bewirkt, dass die **Aufrufliste** Fenster aus, um ein Rollback die Aufrufliste zu dem Punkt, bevor der Ausnahmefehler aufgetreten ist. 

**Warnhinweis anzeigen, wenn keine Symbole beim Starten (nur systemeigen)** wird ein Warnungsdialogfeld angezeigt, wenn Sie versuchen, ein Programm debuggen, für das der Debugger keine Symbolinformationen hat. 

**Warnhinweis anzeigen, wenn Skriptdebugging beim Start deaktiviert ist** wird ein Warndialogfeld angezeigt, wenn der Debugger mit deaktiviertem Skriptdebuggen gestartet wird.

**Verwenden von systemeigenen Kompatibilitätsmodus** , wenn diese Option ausgewählt ist, wird der Debugger den systemeigenen Debugger von Visual Studio 2010 anstelle des neuen nativen Debuggers verwendet.  
  
Beim Debuggen von .NET C++-Code sollten Sie diese Option verwenden, da die neue Debug-Engine das Auswerten von .NET C++-Ausdrücken nicht unterstützt. Durch das Aktivieren des nativen Kompatibilitätsmodus werden aber viele Funktionen deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. Z. B. die legacy-Engine verfügt nicht über viele Schnellansichten für integrierte Typen wie `std::string` in Visual Studio 2015-Projekten.   Verwenden Sie Visual Studio 2013-Projekte für optimales debugging in diesen Fällen an.
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
