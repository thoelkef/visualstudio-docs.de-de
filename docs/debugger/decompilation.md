---
title: Dekompilieren von .NET-Code beim Debuggen | Microsoft Docs
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
ms.openlocfilehash: d63c05120842d52dd54359e128d0cc5f2a195817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508744"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generieren von Quellcode aus .NET-Assemblys während des Debuggens

Beim Debuggen einer .NET-Anwendung stellen Sie möglicherweise fest, dass Sie Quellcode anzeigen möchten, den Sie nicht haben. Beispiel: Aufbrechen einer Ausnahme oder Verwenden der Aufrufliste zum Navigieren zu einem Quellspeicherort.

> [!NOTE]
> * Die Generierung von Quellcode (Dekompilierung) ist nur für .NET-Anwendungen verfügbar und basiert auf dem [Open-Source-ILSpy-Projekt.](https://github.com/icsharpcode/ILSpy)
> * Die Dekompilierung ist nur in Visual Studio 2019 16.5 und höher verfügbar.
> * Durch Das Anwenden des [SuppressIldasmAttribute-Attributs](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) auf eine Assembly oder ein Modul verhindert, dass Visual Studio versucht, eine Dekompilierung zu versuchen.

## <a name="generate-source-code"></a>Generieren von Quellcode

Wenn Sie debuggen und kein Quellcode verfügbar ist, zeigt Visual Studio das Dokument **"Quelle nicht gefunden"** oder, wenn Sie keine Symbole für die Assembly haben, das Dokument **Keine Symbole geladen.** Beide Dokumente verfügen über eine **Decompile-Quellcodeoption,** die C-Code für den aktuellen Speicherort generiert. Der generierte C-Code kann dann wie jeder andere Quellcode verwendet werden. Sie können den Code anzeigen, Variablen überprüfen, Haltepunkte festlegen usw.

### <a name="no-symbols-loaded"></a>Keine Symbole geladen

Die folgende Abbildung zeigt die Meldung **Keine Symbole geladen.**

![Screenshot eines geladenen Symbols](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Quelle nicht gefunden

Die folgende Abbildung zeigt die Meldung **Quelle nicht gefunden.**

![Screenshot des nicht gefundenen Dokuments](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generieren und Einbetten von Quellen für eine Baugruppe

Zusätzlich zum Generieren von Quellcode für einen bestimmten Speicherort können Sie den gesamten Quellcode für eine bestimmte .NET-Assembly generieren. Wechseln Sie dazu zum **Fenster Modules** und aus dem Kontextmenü einer .NET-Assembly, und wählen Sie dann den **Quellcodebefehl Dekompilieren** aus. Visual Studio generiert eine Symboldatei für die Assembly und bettet dann die Quelle in die Symboldatei ein. In einem späteren Schritt können Sie den eingebetteten Quellcode [extrahieren.](#extract-and-view-the-embedded-source-code)

![Screenshot des Assemblykontextmenüs im Modulfenster mit dekompilierendem Quellbefehl.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extrahieren und Anzeigen des eingebetteten Quellcodes

Sie können Quelldateien extrahieren, die in eine Symboldatei eingebettet sind, indem Sie den Befehl **Quellcode extrahieren** im Kontextmenü des **Fensters Modules** verwenden.

![Screenshot des Assemblykontextmenüs im Modulfenster mit dem Befehl Extraktquellen.](media/decompilation-extract-source-code.png)

Die extrahierten Quelldateien werden der Lösung als [verschiedene Dateien](../ide/reference/miscellaneous-files.md)hinzugefügt. Das Feature für verschiedene Dateien ist in Visual Studio standardmäßig deaktiviert. Sie können diese Funktion über das Kontrollkästchen**Environment** >  **Umgebungsdokumente** > **Documents** > für**Tools-Optionen** > **aktivieren, die verschiedene Dateien im Projektmappen-Explorer anzeigen.** Ohne diese Funktion zu aktivieren, können Sie den extrahierten Quellcode nicht öffnen.

![Screenshot der Werkzeugoptionsseite mit aktivierter Option für verschiedene Dateien.](media/decompilation-tools-options-misc-files.png)

Extrahierte Quelldateien werden in den verschiedenen Dateien im **Projektmappen-Explorer**angezeigt.

![Screenshot des Lösungs-Explorers mit verschiedenen Dateien.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Bekannte Einschränkungen

### <a name="requires-break-mode"></a>Erfordert Unterbrechungsmodus

Das Generieren von Quellcode mithilfe der Dekompilierung ist nur möglich, wenn sich der Debugger im Unterbrechungsmodus befindet und die Anwendung angehalten wird. Visual Studio wechselt z. B. in den Unterbrechungsmodus, wenn es auf einen Haltepunkt oder eine Ausnahme trifft. Sie können Visual Studio ganz einfach auslösen, um die nächste![Ausgeführte](media/decompilation-break-all.png)des Codes zu unterbrechen, indem Sie den Befehl **Alle unterbrechen** ( Alle unterbrechungsfest).

### <a name="decompilation-limitations"></a>Dekompilierungseinschränkungen

Das Generieren von Quellcode aus dem Zwischenformat (IL), das in .NET-Assemblys verwendet wird, weist einige inhärente Einschränkungen auf. Daher sieht der generierte Quellcode nicht wie der ursprüngliche Quellcode aus. Die meisten Unterschiede liegen an Orten, an denen die Informationen im ursprünglichen Quellcode zur Laufzeit nicht benötigt werden. Beispielsweise werden Informationen wie Leerzeichen, Kommentare und die Namen lokaler Variablen zur Laufzeit nicht benötigt. Es wird empfohlen, die generierte Quelle zu verwenden, um zu verstehen, wie das Programm ausgeführt wird, und nicht als Ersatz für den ursprünglichen Quellcode.

### <a name="debug-optimized-or-release-assemblies"></a>Debugoptimierte oder Releaseassemblys

Beim Debuggen von Code, der aus einer Assembly dekompiliert wurde, die mithilfe von Compileroptimierungen kompiliert wurde, können die folgenden Probleme auftreten:
- Haltepunkte sind möglicherweise nicht immer an den passenden Beschaffungsstandort gebunden.
- Das Treten kann nicht immer an die richtige Stelle treten.
- Lokale Variablen haben möglicherweise keine genauen Namen.
- Einige Variablen sind möglicherweise nicht für die Auswertung verfügbar.

Weitere Informationen finden Sie in der GitHub-Ausgabe: [ICSharpCode.Decompiler-Integration in VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Dekompilierungszuverlässigkeit

Ein relativ kleiner Prozentsatz der Dekompilierungsversuche kann zu einem Fehler führen. Dies ist auf einen Sequenzpunkt-Null-Referenzfehler in ILSpy zurückzuführen.  Wir haben den Fehler gemildert, indem wir diese Probleme aufgefangen und den Dekompilierungsversuch ordnungsgemäß verfehlt haben.

Weitere Informationen finden Sie in der GitHub-Ausgabe: [ICSharpCode.Decompiler-Integration in VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Einschränkungen mit asynchronem Code

Die Ergebnisse der Dekompilierung von Modulen mit async/await-Codemustern sind möglicherweise unvollständig oder schlagen vollständig fehl. Die ILSpy-Implementierung von async/await und yield state-machines ist nur teilweise implementiert. 

Weitere Informationen finden Sie im GitHub-Problem: [PDB Generator Status](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Nur eigenen Code

Mit den [JMC-Einstellungen (Just My Code)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) kann Visual Studio System-, Framework-, Bibliotheks- und andere Nicht-Benutzeraufrufe schrittweise ausführen. Während einer Debugsitzung zeigt das **Fenster Modules** an, welche Codemodule der Debugger als "Mein Code" (Benutzercode) behandelt.

Die Dekompilierung von optimierten oder Release-Modulen erzeugt Nicht-Benutzercode. Wenn der Debugger z. B. den dekompilierten Nichtbenutzercode auflöst, wird das Fenster **Keine Quelle** angezeigt. Um Nur meinen Code zu deaktivieren, navigieren Sie zu > **Tools-Optionen** (oder **Tools** **Debugoptionen** > **Options**) > **Debuggen** > **von Allgemein**, und deaktivieren Sie dann Nur meinen Code **aktivieren**.

### <a name="extracted-sources"></a>Extrahierte Quellen

Der aus einer Assembly extrahierte Quellcode hat die folgenden Einschränkungen:
- Der Name und speicherort der generierten Dateien sind nicht konfigurierbar.
- Die Dateien sind temporär und werden von Visual Studio gelöscht.
- Die Dateien werden in einem einzigen Ordner abgelegt, und jede Ordnerhierarchie, die die ursprünglichen Quellen hatten, wird nicht verwendet.
- Der Dateiname für jede Datei enthält einen Prüfsummenhash der Datei.

### <a name="generated-code-is-c-only"></a>Generierter Code ist nur C-Code
Die Dekompilierung generiert nur Quellcodedateien in C. Es gibt keine Möglichkeit, Dateien in einer anderen Sprache zu generieren.
