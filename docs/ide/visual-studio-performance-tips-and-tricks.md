---
title: "Tipps und Tricks für die Leistung von Visual Studio | Microsoft-Dokumentation"
ms.date: 08/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: 2fbcb59e-e981-4b40-8b7a-c1140d31ec4b
caps.latest.revision: "1"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 936d0df8c838227c5d6c99b0f04f1069eae8a277
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Tipps und Tricks für die Leistung von Visual Studio

Diese die Leistung von Visual Studio betreffenden Empfehlungen sind für Situationen mit wenig Arbeitsspeicher gedacht, die selten auftreten. In solchen Fällen können Sie bestimmte Funktionen von Visual Studio optimieren, die zu dem Zeitpunkt wahrscheinlich nicht verwendet werden. Die folgenden Tipps sind nicht als allgemeine Empfehlungen gedacht.

> [!NOTE]
> Wenn Sie aufgrund von Speicherproblemen Probleme mit dem Produkt haben, informieren Sie uns über das Feedbacktool.

## <a name="optimize-your-environment"></a>Optimieren der Umgebung

- **Verwenden eines 64-Bit-Betriebssystems**

    Wenn Sie Ihr System von einer 32-Bit-Version von Windows auf eine 64-Bit-Version aktualisieren, erweitern Sie die Menge des für Visual Studio verfügbaren virtuellen Arbeitsspeichers von 2 auf 4 GB. Dadurch kann Visual Studio erheblich größere Workloads verarbeiten, obwohl es sich um einen 32-Bit-Prozess handelt.

    Weitere Informationen finden Sie unter [Memory limits (Arbeitsspeicherbegrenzungen)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa366778(v=vs.85).aspx#memory_limits) und [Using /LARGEADDRESSAWARE on 64-bit Windows (Verwenden von /LARGEADDRESSAWARE unter einer 64-Bit-Version von Windows)](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="configure-solution-and-projects"></a>Konfigurieren von Projektmappen und Projekten

Wenn sie eine sehr große Projektmappe mit vielen Projekten haben, können Sie von den folgenden Optimierungen profitieren:

- **Projekte entladen**

    Sie können selten verwendete, einzelne Projekte im Projektmappen-Explorer mit einem Rechtsklick über das Kontextmenü manuell entladen.

- **Refactoring der Projektmappe**

    Sie können die Projektmappe in mehrere kleinere Projektmappendateien mit häufig verwendeten Projekte aufteilen. Dieses Refactoring sollte den Arbeitsspeicherverbrauch des Workflows erheblich reduzieren. Außerdem werden kleinere Projektmappen schneller geladen.

## <a name="configure-debugging-options"></a>Konfigurieren von Debugoptionen
Wenn Sie in der Regel während des Debuggens von Sitzungen über nicht ausreichend Arbeitsspeicher verfügen, können Sie die Leistung optimieren, indem Sie mindestens eine Konfigurationsänderung vornehmen.

- **Nur meinen Code aktivieren**

    Die einfachste Optimierung ist die Aktivierung der Funktion **Nur eigenen Code**, die nur Symbole für das Projekt lädt. Die Aktivierung dieser Funktion zu erheblichen Arbeitsspeichereinsparungen für das Debuggen von verwalteten Anwendungen (.NET) führen. Diese Option ist in einigen Projekttypen bereits standardmäßig aktiviert.

    Um **Nur eigenen Code** zu aktivieren, wählen Sie **Extras > Optionen > Debugging > Allgemein** und dann **Nur meinen Code aktivieren** aus.

- **Angeben der zu ladenden Symbole**

    Für das native Debuggen ist das Laden von Symboldateien (.pdb) im Hinblick auf die Arbeitsspeicherressourcen teuer. Sie können Ihre Debugsymbol-Einstellungen konfigurieren, um Arbeitsspeicher zu sparen. In der Regel konfigurieren Sie die Projektmappe so, dass nur Module aus Ihrem Projekt geladen werden.

    Wählen Sie zum Laden von Symbolen **Extras > Optionen > Debugging > Symbole** aus.

    Legen Sie die Optionen auf **Nur angegebene Module** anstelle von **Alle Module** fest, und geben Sie die Module an, die geladen werden sollen. Während des Debuggens können Sie im Fenster **Module** auch mit der rechten Maustaste auf bestimmte Module klicken, um ein Modul in den Symbolladeborgang explizit aufzunehmen. Wählen Sie zum Öffnen des Fensters während des Debuggens **Debuggen > Windows > Module** aus.

    Weitere Informationen finden Sie unter [Understanding symbol files (Grundlegendes zu Symboldateien)](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).

- **Deaktivieren von Diagnosetools**

    Es wird empfohlen, die CPU-Profilerstellung nach ihrer Verwendung zu deaktivieren. Diese Funktion kann große Mengen von Ressourcen belegen. Sobald die CPU-Profilerstellung aktiviert ist, wird dieser Status in allen nachfolgenden Debugsitzungen beibehalten. Daher muss sie nach Beendigung explizit deaktiviert werden. Sie können einige Ressourcen speichern, indem Sie während des Debuggens die Diagnosetools deaktivieren, sollten Sie diese Funktionen nicht bereitstellen müssen.

    Um die Diagnosetools zu deaktivieren, starten Sie eine Debugsitzung, wählen Sie **Extras > Optionen > Diagnosetools beim Debuggen aktivieren** aus, und deaktivieren Sie die Option.

    Weitere Informationen finden Sie unter [Profilerstellungstools](https://docs.microsoft.com/en-us/visualstudio/profiling/profiling-tools).

## <a name="disable-tools-and-extensions"></a>Deaktivieren von Tools und Erweiterungen
Einige Tools oder Erweiterungen müssen möglicherweise ausgeschaltet werden, um die Leistung zu verbessern.

> [!TIP]
> Häufig können Sie Leistungsprobleme isolieren, indem Sie Erweiterungen eine nach der anderen deaktivieren und die Leistung immer wieder überprüfen.

### <a name="managed-language-services-roslyn"></a>Dienste für verwaltete Sprachen (Roslyn)

Informationen zu Leistungsüberlegungen hinsichtlich Roslyn finden Sie unter [Performance considerations for large solutions (Leistungsaspekte bei großen Projektmappen)] (https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Deaktivieren der vollständige Projektmappenanalyse**

    Visual Studio analysiert Ihre gesamte Projektmappe, um eine alle Fehler vor dem Erstellen eines Builds zu erfassen. Diese Funktion ist nützlich, um Fehler so früh wie möglich zu identifizieren. Allerdings kann diese Funktion bei sehr großen Projektmappen beträchtliche Arbeitsspeicherressourcen konsumieren. Wenn Sie Arbeitsspeichermangel oder ähnliche Probleme haben, können Sie diese Funktion deaktivieren, um diese Ressourcen freizugeben. Diese Option ist für Visual Basic standardmäßig aktiviert und für C# deaktiviert.

    Um die **vollständige Projektmappenanalyse** zu deaktivieren, wählen Sie **Extras > Optionen > Text-Editor > <Visual Basic oder C#>**. Wählen Sie dann **Erweitert** aus, und deaktivieren das Kontrollkästchen **Enable full solution analysis** (Vollständige Projektmappenanalyse aktivieren).

- **Deaktivieren von CodeLens**

    Visual Studio führt eine Aufgabe **Alle Verweise suchen** für jede Methode aus, während sie angezeigt wird. CodeLens bietet Funktionen wie die Inlineanzeige der Anzahl der Verweise. The work is performed in a separate process (for example, ServiceHub.RoslynCodeAnalysisService32). In sehr großen Projektmappen oder auf Systemen mit eingeschränkten Ressourcen kann diese Funktion entscheidenden Einfluss auf die Leistung haben, obwohl die mit niedriger Priorität ausgeführt wird. Wenn bei diesem Prozess eine hohe CPU-Auslastung oder Probleme mit dem Arbeitsspeicher auftreten (z.B. beim Laden von großen Projektmappen auf einem 4-GB-Computer), können Sie versuchen, durch das Deaktivieren dieser Funktion Ressourcen freizugeben.

    Um CodeLens zu deaktivieren, wählen Sie **Extras > Optionen > Text-Editor > Alle Sprachen > CodeLens** aus, und deaktivieren Sie die Funktion.

    Diese Funktion steht in Visual Studio Professional und Visual Studio Enterprise zur Verfügung.

### <a name="other-tools-and-extensions"></a>Andere Tools und Erweiterungen

- **Deaktivieren von Erweiterungen**

    Erweiterungen sind zusätzliche, zu Visual Studio hinzugefügte Softwarekomponenten, die neue Funktionalität bereitstellen oder vorhandene Funktionalität erweitern. Erweiterungen können häufig eine Quelle von Problemen mit Arbeitsspeicherressourcen sein. Wenn bei Ihnen Arbeitsspeicherprobleme auftreten, deaktivieren Sie die Erweiterungen nacheinander, um die Auswirkungen auf das Szenario oder den Workflow zu beobachten.

    Um Erweiterungen zu deaktivieren, wechseln Sie zu **Tools | Erweiterungen und Updates**, und deaktivieren eine bestimmte Erweiterung.

- **Deaktivieren des XAML-Designers**

    Der XAML-Designer ist standardmäßig aktiviert. Es werden aber nur Ressourcen belegt, wenn Sie eine XAML-Datei öffnen. Wenn Sie mit XAML-Dateien arbeiten, den Designer aber nicht verwenden möchten, deaktivieren Sie diese Funktion, um Arbeitsspeicher freizugeben.

    Um den XAML-Designer zu deaktivieren, wechseln Sie zu **Tools > Optionen > XAML-Designer > XAML-Designer aktivieren**, und deaktivieren Sie die Option.

- **Entfernen von Workloads**

    Sie können den Visual Studio-Installer verwenden, um Workloads zu entfernen, die nicht mehr verwendet werden. Dadurch kann Ihre Start- und Laufzeitkosten zu optimieren, indem Pakete und Assemblys übersprungen werden, die nicht mehr benötigt werden.

## <a name="force-a-garbage-collection"></a>Erzwingen einer Garbage Collection

Die CLR verwendet eine Arbeitsspeicherverwaltungssystem mit Garbage Collection. In diesem System wird manchmal Speicher von Objekten belegt, die nicht mehr benötigt werden. Dieser Status ist vorübergehend. Der Garbage Collector gibt diesen Arbeitsspeicher basierend auf dessen Leistungs- und Ressourcenverwendungsheuristik frei. Sie können die CLR mit einem Hotkey in Visual Studio zwingen, nicht verwendeten Arbeitsspeicher zu sammeln. Wenn die Menge an nicht verwendeten Objekten bereits sehr groß ist und Sie eine Garbage Collection erzwingen, sollten Sie im Task-Manager sehen können, wie die Arbeitsspeicherauslastung des Prozesses „devenv.exe“ abnimmt. Es ist aber nur selten notwendig, diese Methode anzuwenden. Nachdem jedoch ein teurer Vorgang (z.B. ein vollständiger Build, eine Debugsitzung oder ein Ereignis in einer offenen Projektmappe) abgeschlossen wurde, kann Ihnen die Methode dabei helfen zu bestimmen, wie viel Arbeitsspeicher tatsächlich vom Prozess verwendet wird. Da Visual Studio (verwaltetes & nativ) kombiniert wird, ist es gelegentlich möglich, dass die native Zuweisung und der Garbage Collector um begrenzte Arbeitsspeicherressourcen konkurrieren. Bei hoher Arbeitsspeicherauslastung kann es hilfreich sein, die Ausführung des Garbage Collectors zu erzwingen.

Um eine automatische Speicherbereinigung zu erzwingen, verwenden Sie den Hotkey: **STRG+ALT+UMSCHALTTASTE+F12**, **STRG+ALT+UMSCHALTTASTE+F12** (zweimal drücken).

Wenn das Erzwingen der Garbage Collection zur zuverlässigen Funktion Ihres Szenarios führt, übermitteln Sie uns einen Bericht über die Visual Studio-Feedbacktool, denn dieses Verhalten ist wahrscheinlich ein Fehler.

Eine ausführliche Beschreibung des CLR-Garbage Collectors finden Sie unter [Fundamental of Garbage Collection (Grundlagen der Garbage Collection)](https://msdn.microsoft.com/en-us/library/ee787088(v=vs.110).aspx).

## <a name="see-also"></a>Siehe auch  
 [Visual Studio-IDE](../ide/index.md)
