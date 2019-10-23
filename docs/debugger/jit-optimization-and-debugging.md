---
title: JIT-Optimierung und-Debuggen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12752acf75da70fa30666f9b1780256c94bde859
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731624"
---
# <a name="jit-optimization-and-debugging"></a>JIT-Optimierung und -Debuggen
**Funktionsweise von Optimierungen in .net:** Wenn Sie versuchen, Code zu debuggen, ist es einfacher, wenn der Code **nicht** optimiert wird. Dies liegt daran, dass beim Optimieren von Code der Compiler und die Laufzeit Änderungen am ausgegebenen CPU-Code vornehmen, sodass er schneller ausgeführt wird, aber eine geringere direkte Zuordnung zum ursprünglichen Quellcode aufweist. Dies bedeutet, dass Debugger häufig nicht den Wert lokaler Variablen erkennen können, und Code Schritte und Haltepunkte funktionieren möglicherweise nicht wie erwartet.

Normalerweise erstellt die releasebuildkonfiguration optimierten Code und die Debug-Buildkonfiguration nicht. Die `Optimize` MSBuild-Eigenschaft steuert, ob der Compiler aufgefordert wird, Code zu optimieren.

Im .NET-Ökosystem wird Code in einem zweistufigen Prozess von der Quelle in die CPU-Anweisungen umgewandelt: zunächst konvertiert C# der Compiler den Text, den Sie eingeben, in eine binäre Binär Form namens MSIL und schreibt diese in DLL-Dateien. Später konvertiert die .NET-Laufzeit diese MSIL in die CPU-Anweisungen. Beide Schritte können zu einem gewissen Grad optimiert werden, aber der zweite Schritt, der von der .NET-Runtime ausgeführt wird, führt zu den signifikanteren Optimierungen.

**Die Option "JIT-Optimierung beim Laden von Modulen unterdrücken (nur verwaltet)":** Der Debugger macht eine Option verfügbar, die steuert, was geschieht, wenn eine mit Optimierungen kompilierte DLL innerhalb des Ziel Prozesses geladen wird. Wenn diese Option deaktiviert ist (Standardzustand), werden die Optimierungen beim Kompilieren des MSIL-Codes in den CPU-Code von der .NET-Runtime aktiviert. Wenn die Option aktiviert ist, fordert der Debugger an, dass Optimierungen deaktiviert werden.

Wenn Sie die Option **JIT-Optimierung beim Laden von Modulen unterdrücken (nur verwaltet)** suchen möchten, wählen Sie Extras  > **Optionen**aus, und **Wählen Sie dann** unter dem Knoten **Debuggen** die Seite **Allgemein** aus.

**Wann sollten Sie diese Option aktivieren:** Aktivieren Sie diese Option, wenn Sie die DLLs aus einer anderen Quelle (z. b. einem nuget-Paket) heruntergeladen haben und den Code in dieser DLL debuggen möchten. Damit dies funktioniert, müssen Sie auch die Symbol Datei (PDB-Datei) für diese dll finden.

Wenn Sie nur den Code debuggen möchten, den Sie lokal aufbauen, empfiehlt es sich, diese Option nicht zu deaktivieren. in manchen Fällen wird das Debuggen durch Aktivieren dieser Option erheblich verlangsamt. Für diese langsame Verlangsamung gibt es zwei Gründe:

* Optimierter Code wird schneller ausgeführt. Wenn Sie Optimierungen für viele Code deaktivieren, kann sich dies auf die Leistung auswirken.
* Wenn nur eigenen Code aktiviert ist, lädt der Debugger nicht einmal die Symbole für DLLs, die optimiert sind. Das Auffinden von Symbolen kann viel Zeit in Anspruch nehmen.

**Einschränkungen für diese Option:** Es gibt zwei Situationen, in denen diese Option **nicht** funktioniert:

1. In Situationen, in denen der Debugger an einen bereits laufenden Prozess angefügt wird, hat diese Option keine Auswirkungen auf Module, die zum Zeitpunkt der angefügten Debuggers bereits geladen wurden.
2. Diese Option hat keine Auswirkung auf DLLs, die in System eigenem Code vorkompiliert wurden (a. k. a ngen ' ed '). Sie können jedoch die Verwendung von vorkompiliertem Code deaktivieren, indem Sie den Prozess mit der Umgebungsvariable "COMPlus_ZapDisable" auf "1" starten.

## <a name="see-also"></a>Siehe auch
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)
- [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Der verwaltete Ausführungsprozess](/dotnet/standard/managed-execution-process)
