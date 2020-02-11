---
title: Dekompilieren von .NET-Code beim Debuggen | Microsoft-Dokumentation
ms.date: 2/2/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: ffd5f2e4bfc13f79b519fbdf9b3cf517793cd324
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091873"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Quellcode aus .NET-Assemblys beim Debuggen generieren

Wenn Sie eine .NET-Anwendung debuggen, können Sie möglicherweise Quellcode anzeigen, den Sie nicht besitzen. Beispielsweise das Unterbrechen einer Ausnahme oder die Verwendung der-aufrufsstapel, um zu einem Quell Speicherort zu navigieren.

> [!NOTE]
> * Die Quell Codegenerierung (Dekompilierung) ist nur für .NET-Anwendungen verfügbar und basiert auf dem Open-Source- [ilspy](https://github.com/icsharpcode/ILSpy) -Projekt.
> * Die decokompilierung ist nur in Visual Studio 2019 16,5 und höher verfügbar.

## <a name="generate-source-code"></a>Quellcode generieren

Wenn Sie Debuggen und kein Quellcode verfügbar ist, zeigt Visual Studio das Dokument " **Quelle nicht gefunden** " an. Wenn Sie keine Symbole für die Assembly haben, wird das Dokument " **keine Symbole geladen** " angezeigt. Beide Dokumente haben eine **dekompilierungs Quell Code** Option, C# die Code für den aktuellen Speicherort generiert. Der generierte C# Code kann dann wie jeder andere Quellcode verwendet werden. Sie können den Code anzeigen, Variablen überprüfen, Breakpoints festlegen usw.

### <a name="no-symbols-loaded"></a>Keine Symbole geladen.

In der folgenden Abbildung wird die Meldung " **keine Symbole geladen** " angezeigt.

![Screenshot des Dokuments "kein Symbol geladen"](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Quelle nicht gefunden

In der folgenden Abbildung wird die Meldung **Quelle nicht gefunden** angezeigt.

![Screenshot des Dokuments "Quelle nicht gefunden"](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generieren und Einbetten von Quellen für eine Assembly

Zusätzlich zum Generieren von Quellcode für einen bestimmten Speicherort können Sie den gesamten Quellcode für eine bestimmte .NET-Assembly generieren. Wechseln Sie zu diesem Zweck zum Fenster " **Module** " und im Kontextmenü einer .NET-Assembly, und wählen Sie dann den Befehl " **Quell Code dekompilieren** " aus. Visual Studio generiert eine Symbol Datei für die Assembly und bettet dann die Quelle in die Symbol Datei ein. In einem späteren Schritt können Sie den eingebetteten Quellcode [extrahieren](#extract-and-view-the-embedded-source-code) .

![Screenshot des Kontextmenüs der Assembly im Fenster "Module" mit dem Befehl "dekompilieren Source".](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extrahieren und Anzeigen des eingebetteten Quellcodes

Sie können Quelldateien extrahieren, die in eine Symbol Datei eingebettet sind. verwenden Sie dazu den Befehl **Quell Code extrahieren** im Kontextmenü des Fensters **Module** .

![Screenshot des Kontextmenüs der Assembly im Fenster "Module" mit dem Befehl "Quellen extrahieren".](media/decompilation-extract-source-code.png)

Die extrahierten Quelldateien werden der Projekt Mappe als [sonstige Dateien](../ide/reference/miscellaneous-files.md)hinzugefügt. Die Funktion "sonstige Dateien" ist in Visual Studio standardmäßig deaktiviert. Sie können diese Funktion über das Kontroll **Kästchen Extras > ** **Optionen** > **Umgebung** > **Dokumente** > andere **Dateien in Projektmappen-Explorer anzeigen** aktivieren. Wenn Sie diese Funktion nicht aktivieren, können Sie den extrahierten Quellcode nicht öffnen.

![Screenshot der Optionsseite "Tools" mit aktivierter Option "sonstige Dateien".](media/decompilation-tools-options-misc-files.png)

Extrahierte Quelldateien werden in den verschiedenen Dateien in **Projektmappen-Explorer**angezeigt.

![Screenshot des Projektmappen-Explorers mit verschiedenen Dateien.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Bekannte Einschränkungen

### <a name="requires-break-mode"></a>Erfordert den Break-Modus

Das Erstellen von Quellcode mithilfe der Dekompilierung ist nur möglich, wenn sich der Debugger im Break-Modus befindet und die Anwendung angehalten wurde. Beispielsweise wechselt Visual Studio in den Unterbrechungs Modus, wenn ein Breakpoint oder eine Ausnahme erreicht wird. Sie können mit dem Befehl **alle** Abbrechen (![Symbol "Alle unterbrechen"](media/decompilation-break-all.png)) problemlos Visual Studio veranlassen, den Code bei der nächsten Ausführung des Codes zu unterbrechen.

### <a name="decompilation-limitations"></a>Außerilkompilierungs Einschränkungen

Das Erzeugen von Quellcode aus dem zwischen Format (IL), das in .NET-Assemblys verwendet wird, hat einige inhärente Einschränkungen. Daher sieht der generierte Quellcode nicht wie der ursprüngliche Quellcode aus. Der größte Unterschied besteht darin, dass die Informationen im ursprünglichen Quellcode zur Laufzeit nicht benötigt werden. Beispielsweise werden Informationen wie Leerraum, Kommentare und die Namen lokaler Variablen zur Laufzeit nicht benötigt. Es wird empfohlen, dass Sie die generierte Quelle verwenden, um zu verstehen, wie das Programm ausgeführt wird, und nicht als Ersatz für den ursprünglichen Quellcode.

### <a name="debug-optimized-or-release-assemblies"></a>Debug-oder releaseassemblys

Beim dekompilieren von Code, der aus einer Assembly dekompiliert wurde, die mithilfe von Compileroptimierungen kompiliert wurde, können die folgenden Probleme auftreten:
- Haltepunkte werden möglicherweise nicht immer an den entsprechenden Sourcing-Speicherort gebunden.
- Beim schrittweisen Ausführen des Schritts wird möglicherweise nicht immer der richtige Speicherort
- Lokale Variablen weisen möglicherweise keine genauen Namen auf.

Weitere Informationen finden Sie im GitHub-Problem: [ichsarpcompiler. Decompiler-Integration in VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="extracted-sources"></a>Extrahierte Quellen

Der Quellcode, der aus einer Assembly extrahiert wurde, weist die folgenden Einschränkungen auf:
- Der Name und der Speicherort der generierten Dateien sind nicht konfigurierbar.
- Die Dateien sind temporär und werden von Visual Studio gelöscht.
- Die Dateien werden in einem einzelnen Ordner und in der Ordnerhierarchie abgelegt, in der die ursprünglichen Quellen nicht verwendet wurden.
- Der Dateiname für jede Datei enthält einen Prüfsummen Hash der Datei.

### <a name="generated-code-is-c-only"></a>Generierter Code C# ist nur
Bei der Dekompilierung werden nur Quell C#Code Dateien in generiert. Es gibt keine Option zum Generieren von Dateien in einer anderen Sprache.