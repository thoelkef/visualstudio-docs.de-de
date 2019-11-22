---
title: Dialogfeld "Fehlermeldung bearbeiten und Fortfahren" | Microsoft-Dokumentation
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7df95eae689f7c3abbb0d75a7557ce749bdceee5
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188234"
---
# <a name="edit-and-continue-error-message"></a>Fehlermeldung "Bearbeiten und Fortfahren"

Das Feld Fehlermeldung **Bearbeiten und Fortfahren** wird angezeigt, wenn Sie in einer Codesprache Debuggen, die bearbeiten und Fortfahren unterstützt, aber bearbeiten und Fortfahren für die von Ihnen vorgenommenen Codeänderungen nicht verfügbar ist. Eine ausführlichere Erläuterung finden Sie in der Fehlermeldung. Um auf das Dialogfeld zu reagieren, wählen Sie **OK** aus, um das Dialogfeld zu schließen und den Bearbeitungs Versuch abzubrechen.

Mögliche Ursachen für diese Fehlermeldung:

- Es wird versucht, SQL Server Code zu bearbeiten.
- Es wird versucht, optimierten Code zu bearbeiten. Möglicherweise müssen Sie von einem Releasebuild zu einem Debugbuild wechseln.
- Es wird versucht, Code zu bearbeiten, während er ausgeführt wird, anstatt im Debugger angehalten zu werden. Versuchen Sie, [einen Haltepunkt festzulegen](../debugger/using-breakpoints.md)und den Code zu bearbeiten, während er angehalten wurde.
- Es wird versucht, verwalteten Code zu bearbeiten, wenn nur nicht verwaltetes Debugging aktiviert ist. "Bearbeiten und Fortfahren" funktioniert nicht mit [Debuggen im gemischten Modus](../debugger/how-to-debug-in-mixed-mode.md).
- Vornehmen einer Codeänderung, die von "Bearbeiten und Fortfahren" in der Programmiersprache nicht unterstützt wird. Weitere Informationen finden Sie in den Artikeln über [unterstützte Code C#Änderungen in ](supported-code-changes-csharp.md), [nicht unterstützte Bearbeitungen in Visual Basic bearbeiten und Fortfahren](supported-code-changes-csharp.md)sowie [unterstützte C++ Codeänderungen](supported-code-changes-cpp.md).
- Sie versuchen, Code in einer APP zu bearbeiten, an die Sie angefügt sind, anstatt das Debuggen im Menü **Debuggen** zu starten
- Versuch, Code zu bearbeiten, während ein Dr. Watson-Dump debuggt wird.
- Der Versuch, Code zu bearbeiten, nachdem eine nicht behandelte Ausnahme aufgetreten ist, und die Option zum Entladen **der aufrufsstapel bei nicht behandelten Ausnahmen** ist nicht ausgewählt.
- Beim Debuggen einer eingebetteten Lauf Zeit Anwendung wird versucht, Code zu bearbeiten.
- Es wird versucht, verwalteten Code mit einer .NET Framework-Version vor 4.5.1 mit einem 64-Bit-App-Ziel zu bearbeiten. Wenn Sie "Bearbeiten und Fortfahren" für .NET Framework vor "4.5.1" verwenden möchten, legen Sie das Ziel auf **x86** auf der Registerkarte **\<ProjectName >**  > **Eigenschaften** > Registerkarte **Kompilieren** , **Erweiterte Compilereinstellung**
- Es wurde versucht, Code in einer Assembly zu bearbeiten, die während des Debuggens geändert wurde und erneut geladen wurde.
- Es wird versucht, Code in einer Assembly zu bearbeiten, die noch nicht geladen wurde.
- Das Debuggen einer alten Version einer APP wird gestartet, da die neueste Version Buildfehler aufweist.

Weitere Informationen finden Sie unter:
- [C++Blogbeitrag "Bearbeiten und Fortfahren"](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md)
- [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md)