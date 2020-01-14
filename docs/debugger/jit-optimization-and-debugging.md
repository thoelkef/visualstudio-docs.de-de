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
ms.openlocfilehash: ae11860aaa64448cd4d23b5602cf4c2da1575ce3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916236"
---
# <a name="jit-optimization-and-debugging"></a>JIT-Optimierung und -Debuggen
Wenn Sie versuchen, Code zu debuggen, ist es einfacher, wenn der Code **nicht** optimiert wird. Wenn der Code optimiert ist, nehmen der Compiler und die Laufzeit Änderungen am ausgegebenen CPU-Code vor, sodass er schneller ausgeführt wird, aber eine geringere direkte Zuordnung zum ursprünglichen Quellcode aufweist. Wenn die Zuordnung weniger direkt ist, können Debugger häufig nicht den Wert lokaler Variablen erkennen, und Code Schritte und Breakpoints funktionieren möglicherweise nicht wie erwartet.

> [!NOTE]
> Weitere Informationen zum JIT-Debuggen (Just-in-Time) finden Sie in [dieser Dokumentation](../debugger/debug-using-the-just-in-time-debugger.md).

## <a name="how-optimizations-work-in-net"></a>Funktionsweise von Optimierungen in .net 
Normalerweise erstellt die releasebuildkonfiguration optimierten Code und die Debug-Buildkonfiguration nicht. Die `Optimize` MSBuild-Eigenschaft steuert, ob der Compiler aufgefordert wird, Code zu optimieren.

Im .NET-Ökosystem wird Code aus den Quell-zu-CPU-Anweisungen in einem zweistufigen Prozess umgewandelt: zuerst C# konvertiert der Compiler den Text, den Sie eingeben, in eine binäre Binär Form mit dem Namen "MSIL" und schreibt die MSIL-Datei in DLL-Dateien. Später konvertiert die .NET-Laufzeit diese MSIL in die CPU-Anweisungen. Beide Schritte können zu einem gewissen Grad optimiert werden, aber der zweite Schritt, der von der .NET-Runtime ausgeführt wird, führt zu den signifikanteren Optimierungen.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>Die Option "JIT-Optimierung beim Laden von Modulen unterdrücken (nur verwaltet)"
Der Debugger macht eine Option verfügbar, die steuert, was geschieht, wenn eine mit Optimierungen kompilierte DLL innerhalb des Ziel Prozesses geladen wird. Wenn diese Option deaktiviert ist (Standardzustand), werden die Optimierungen beim Kompilieren des MSIL-Codes in den CPU-Code von der .NET-Runtime aktiviert. Wenn die Option aktiviert ist, fordert der Debugger an, dass Optimierungen deaktiviert werden.

Wenn Sie die Option **JIT-Optimierung beim Laden von Modulen unterdrücken (nur verwaltet)** suchen möchten, wählen Sie Extras > **Optionen**aus, und **Wählen Sie dann** unter dem Knoten **Debuggen** die Seite **Allgemein** aus.

![JIT-Optimierung unterdrücken](../debugger/media/suppress-jit-tool-options.png "JIT-Optimierung unterdrücken")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>Wann sollten Sie die Option "JIT-Optimierung unterdrücken" aktivieren?
Aktivieren Sie diese Option, wenn Sie die DLLs aus einer anderen Quelle (z. b. einem nuget-Paket) heruntergeladen haben und den Code in dieser DLL debuggen möchten. Damit die Unterdrückung funktioniert, müssen Sie auch die Symbol Datei (PDB-Datei) für diese dll finden.

Wenn Sie nur den Code debuggen möchten, den Sie lokal aufbauen, empfiehlt es sich, diese Option nicht zu deaktivieren. in manchen Fällen wird das Debuggen durch Aktivieren dieser Option erheblich verlangsamt. Hierfür gibt es zwei Gründe:

* Optimierter Code wird schneller ausgeführt. Wenn Sie Optimierungen für viele Code deaktivieren, kann sich dies auf die Leistung auswirken.
* Wenn nur eigenen Code aktiviert ist, versucht der Debugger nicht einmal, Symbole für optimierte DLLs zu laden. Das Auffinden von Symbolen kann viel Zeit in Anspruch nehmen.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>Einschränkungen der Option "JIT-Optimierung unterdrücken" 
Es gibt zwei Situationen, in denen das Aktivieren dieser Option **nicht** funktioniert:

1. In Situationen, in denen der Debugger an einen bereits laufenden Prozess angefügt wird, hat diese Option keine Auswirkungen auf Module, die zum Zeitpunkt der angefügten Debuggers bereits geladen wurden.
2. Diese Option hat keine Auswirkung auf DLLs, die in System eigenem Code vorkompiliert wurden (a. k. a ngen ' ed '). Sie können jedoch die Verwendung von vorkompiliertem Code deaktivieren, indem Sie den Prozess mit der Umgebungsvariablen **"COMPlus_ReadyToRun"** auf **"0"** festlegen. Dadurch wird der .net Core-Laufzeit mitgeteilt, die Verwendung von vorkompilierten Images zu deaktivieren und die Laufzeit in JIT-Kompilierungs-Framework-Code zu erzwingen. 

    > [!IMPORTANT]
    > Wenn Sie .NET Framework oder eine ältere Version von .net Core (2. x oder niedriger) als Ziel festlegen, fügen Sie auch die Umgebungsvariable "COMPlus_ZapDisable" hinzu, und legen Sie Sie auf "1" fest.

    **So legen Sie eine Umgebungsvariable für ein .net Core-Projekt in Visual Studio fest:**
    1. Klicken Sie im **Projektmappen-Explorer**mit der **rechten Maustaste auf** die Projektdatei, und wählen Sie **Eigenschaften**aus.
    2. Navigieren Sie zur Registerkarte **Debuggen** , und klicken Sie unter **Umgebungsvariablen**auf die Schaltfläche **Hinzufügen** .
    3. Legen Sie Name (Key) auf **COMPlus_ReadyToRun** fest, und legen Sie den Wert auf **0**fest.

    ![COMPlus_ReadyToRun Umgebungsvariable festlegen](../debugger/media/environment-variables-debug-menu.png "COMPlus_ReadyToRun Umgebungsvariable festlegen")

## <a name="see-also"></a>Siehe auch
- [Debuggen der DotNet Framework-Quelle](../debugger/how-to-debug-dotnet-framework-source.md)
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)
- [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Der verwaltete Ausführungsprozess](/dotnet/standard/managed-execution-process)
