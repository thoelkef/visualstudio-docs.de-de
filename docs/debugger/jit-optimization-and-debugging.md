---
title: JIT-Optimierung und-Debuggen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a9b18ab38c7c19fa5208d34439bd3133099e8bc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477354"
---
# <a name="jit-optimization-and-debugging"></a>JIT-Optimierung und -Debuggen
**Funktionsweise von Optimierungen in .NET:** , wenn Sie versuchen, Code zu debuggen, es ist einfacher bei, dass Code **nicht** optimiert. Dies liegt daran, wenn Code optimiert wird, der Compiler und die Laufzeit der ausgegebene Code für die CPU-ändern, damit schneller ausgeführt werden, aber eine weniger direkte Zuordnung zu den ursprünglichen Quellcode hat. Dies bedeutet, dass der Debugger sind häufig nicht Aufschluss über den Wert der lokalen Variablen und code schrittweise durchlaufen und Haltepunkte funktionieren möglicherweise nicht wie erwartet.

Normalerweise die Releasebuildkonfiguration optimierten Code erstellt, und die Debug-Buildkonfiguration nicht. Die `Optimize` MSBuild-Eigenschaft steuert, ob der Compiler angewiesen wird, um Code zu optimieren.

Das Ökosystem .NET Code von Quell-zu CPU-Anweisungen in einem zweistufigen Prozess aktiviert ist: zuerst der C#-Compiler den eingegebene Text in einen intermediate Binärformat aufgerufen MSIL konvertiert, und dies auf DLL-Dateien schreibt. Später, konvertiert der .NET Common Language Runtime diese MSIL in CPU-Anweisungen. Beide Schritte in gewissem Umfang optimieren können, aber der zweite Schritt ausgeführt, die von der .NET Common Language Runtime führt die aussagekräftigeren Optimierungen.

**Die Optimierungsoption "Unterdrücken JIT-beim Laden von Modulen (nur verwaltet)":** der Debugger eine Option, die steuert, was geschieht, wenn eine DLL, die mit aktivierten Optimierungen kompiliert wird innerhalb der Zielprozess geladen verfügbar gemacht. Wenn diese Option deaktiviert ist (Standardstatus), und klicken Sie dann den MSIL-Code in CPU-Code von der .NET Common Language Runtime kompiliert wird, die Optimierungen aktiviert bleibt. Wenn die Option aktiviert ist, fordert der Debugger, dass die Optimierungen deaktiviert.

Die **unterdrücken JIT-Optimierung beim Laden von Modulen (nur verwaltet)** Option finden Sie auf der **allgemeine** Seite der **Debuggen** Knoten in der **Optionen** (Dialogfeld).

**Wann sollten Sie diese Option aktivieren:** aktivieren Sie diese Option aus, wenn Sie die DLLs aus einer anderen Quelle, z. B. ein Nuget-Paket heruntergeladen haben, und Sie den Code in dieser DLL debuggen möchten. Damit dies funktioniert müssen Sie auch die Symboldatei (PDB) für diese DLL suchen.

Wenn Sie nur von Interesse Debuggen des Codes, die Sie lokal erstellen sind, empfiehlt es sich, diese Option deaktiviert, da in einigen Fällen die Aktivierung dieser Option bedeutend Debuggen verlangsamt wird. Es gibt zwei Grund dafür verlangsamen:

* Optimierter Code schneller ausgeführt. Wenn Sie deaktiviert Optimierungen für viele Code aktivieren, kann die Auswirkungen auf die Leistung summieren.
* Wenn Sie nur mein Code aktiviert haben, wird auch nicht der Debugger versuchen und Laden Sie Symbole für DLL-Dateien, die optimiert werden. Suchen von Symbolen kann sehr lange dauern.

**Einschränkungen für diese Option:** es gibt zwei Situationen, in denen bei dieser Option wird **nicht** arbeiten:

1. In Situationen, in dem Sie den Debugger an einem bereits laufenden Prozess anfügen, müssen diese Option keine Auswirkungen auf Module, die bereits zum Zeitpunkt geladen wurden, die der Debugger angefügt wurde.
2. Diese Option wirkt sich nicht auf DLLs, die wurden bereits in nativen Code kompiliert (bzw. mit NGen verarbeitet). Sie können jedoch Verwendung von vorkompilierter Code deaktivieren, durch Starten des Prozesses mit der Umgebung die Variable "COMPlus_ZapDisable" auf "1" festgelegt.

## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Fügen an laufende Prozesse an](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Der verwaltete Ausführungsprozess](/dotnet/standard/managed-execution-process)
