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
ms.openlocfilehash: 7346b6fd8fbd483021437638f9e134ead88a0b93
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699144"
---
# <a name="jit-optimization-and-debugging"></a>JIT-Optimierung und -Debuggen
**Funktionsweise von Optimierungen in .NET:** , wenn Sie versuchen, Code zu debuggen, es ist einfacher bei, dass Code **nicht** optimiert. Das liegt bei der Code optimiert, Compiler und Laufzeit Änderungen an der ausgegebene Code für die CPU-vornehmen, damit sie schneller ausgeführt, aber eine weniger direkte Zuordnung zu den ursprünglichen Quellcode hat. Dies bedeutet, dass der Debugger sind häufig nicht teilen Sie den Wert der lokalen Variablen und code durchlaufen und Haltepunkte funktionieren möglicherweise nicht wie erwartet.

Normalerweise die Release-Buildkonfiguration erstellt optimierten Code und die Debug-Buildkonfiguration nicht. Die `Optimize` MSBuild-Eigenschaft steuert, ob der Compiler angewiesen wird, um Code zu optimieren.

Im .NET-Ökosystem, Code aus der Quelle um CPU-Anweisungen in einem zweistufigen Prozess aktiviert ist: zuerst die C# Compiler den eingegebene Text in ein vorläufiges binäre Formular wird aufgerufen, MSIL konvertiert und schreibt diese in der DLL-Dateien. Später in .NET Runtime diese MSIL konvertiert, um CPU-Anweisungen. Beide Schritte zu einem gewissen Grad optimieren können, aber der zweite Schritt ausgeführt, die von der .NET-Laufzeit führt die wichtigeren Optimierungen.

**Die Option "Unterdrücken JIT-Optimierung beim Laden von Modulen (nur verwaltet)":** Debugger stellt eine Option, die steuert, was geschieht, wenn eine DLL, die mit aktivierten Optimierungen kompiliert wird in den Zielprozess geladen. Wenn diese Option deaktiviert ist (Standardstatus), und klicken Sie dann in CPU-Code den MSIL-Code für die .NET Runtime kompiliert wird, die Optimierungen aktiviert bleiben. Wenn die Option aktiviert ist, fordert dann der Debugger an, dass Optimierungen deaktiviert werden.

Finden der **unterdrücken JIT-Optimierung beim Laden von Modulen (nur verwaltet)** wählen Option **Tools** > **Optionen**, und wählen Sie dann die  **Allgemeine** Seite die **Debuggen** Knoten.

**Wann sollten Sie diese Option überprüfen:** aktivieren Sie diese Option aus, wenn Sie die DLLs aus einer anderen Quelle, z. B. einem Nuget-Paket heruntergeladen haben, und Sie den Code in dieser DLL debuggen möchten. Damit dies funktioniert müssen Sie auch die Symboldatei (PDB) für diese DLL finden.

Wenn Sie nur den Code, den Sie lokal erstellen debuggen möchten, empfiehlt es sich, diese Option deaktiviert, da in einigen Fällen durch Aktivieren dieser Option bedeutend Debuggen verlangsamt wird. Es gibt zwei Grund Verlangsamung:

* Optimierter Code schneller ausgeführt. Wenn Sie deaktiviert Optimierungen für viel Code eingeschaltet sind, kann die Auswirkungen auf die Leistung summieren.
* Wenn Sie nur mein Code aktiviert haben, wird der Debugger nicht einmal versuchen Sie es und Laden von Symbolen für DLLs, die optimiert werden. Suchen von Symbolen kann sehr lange dauern.

**Einschränkungen für diese Option:** es gibt zwei Situationen, in denen bei dieser Option wird **nicht** arbeiten:

1. In Situationen, in dem Sie den Debugger an einem bereits laufenden Prozess anfügen, müssen diese Option keine Auswirkungen auf die Module, die bereits zum Zeitpunkt geladen wurden, die der Debugger angefügt wurde.
2. Diese Option hat keine Auswirkungen auf DLLs, die wurden vorab in nativen Code kompiliert (bzw. mit NGen verarbeitet). Allerdings können Sie Verwendung von vorab kompilierter Code deaktivieren, durch den Prozess starten, mit der Umgebung, die Variable "COMPlus_ZapDisable' auf '1' festgelegt.

## <a name="see-also"></a>Siehe auch
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)
- [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Der verwaltete Ausführungsprozess](/dotnet/standard/managed-execution-process)
