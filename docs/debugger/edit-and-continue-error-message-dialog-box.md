---
title: Bearbeiten und Fortfahren Fehlermeldungsdialogfeld | Microsoft-Dokumentation
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
ms.openlocfilehash: 0428ecf21da525b8f77334e57547c8f10da7cdf5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044902"
---
# <a name="edit-and-continue-error-message"></a>Bearbeiten Sie und fortfahren Sie-Fehlermeldung

Die **bearbeiten und Fortfahren** Fehlermeldungsfeld angezeigt wird, wenn Sie in einer Codesprache Debuggen, das Bearbeiten und Fortfahren unterstützt, aber bearbeiten und fortfahren, ist nicht verfügbar für die codeänderungen, die Sie vorgenommen haben. Die Fehlermeldung enthält eine ausführlichere Erläuterung. Wählen Sie zum Dialogfeld für die Antwort **OK** , um das Dialogfeld schließen und die Bearbeitungsversuch Abbrechen.

Mögliche Ursachen für diese Fehlermeldung

- Möchten SQL Server-Code bearbeiten.
- Versucht, optimierten Code zu bearbeiten. Sie müssen möglicherweise aus einem versionsbuild in einem Debugbuild zu wechseln.
- Versucht, Code zu bearbeiten, während er ausgeführt wird, anstatt während der Unterbrechung im Debugger. Versuchen Sie es [Festlegen eines Haltepunkts](../debugger/using-breakpoints.md), und Bearbeiten des Codes während angehalten.
- Möchten verwalteten Code zu bearbeiten, wenn nur nicht verwaltetes debugging aktiviert ist. Bearbeiten und Fortfahren funktioniert nicht mit [Debuggen im gemischten Modus](../debugger/how-to-debug-in-mixed-mode.md).
- Vornehmen der Änderung wird nicht in einer Programmiersprache bearbeiten und Fortfahren unterstützt. Weitere Informationen finden Sie in Artikeln über [unterstützte codeänderungen in C# ](supported-code-changes-csharp.md), [nicht unterstützte Bearbeitungen in Visual Basic zu bearbeiten und Fortfahren](/visualstudio/debugger/supported-code-changes-csharp), und [unterstützt C++-Code-Änderungen](supported-code-changes-cpp.md).
- Versucht, Code in einer app zu bearbeiten, Sie, angefügt sind, statt von Debuggen, die **Debuggen** Menü.
- Versucht, Code zu bearbeiten, während des Debuggens einer Notfallwiederherstellung. Watson-Sicherungskopie.
- Versucht, Code zu bearbeiten, nachdem eine unbehandelte Ausnahme auftritt und die Option **Aufrufliste für Ausnahmefehler entladen** nicht ausgewählt ist.
- Versucht, Code zu bearbeiten, während des Debuggens einer eingebetteten Laufzeitanwendung.
- Möchten verwalteten Code verwenden eine Version von .NET Framework 4.5.1 vor mit einer 64-Bit-Anwendung zu bearbeiten. Zum Bearbeiten und Fortfahren für .NET Framework 4.5.1 vor verwenden, legen Sie das Ziel auf **X86** in die  **\<Projektname >** > **Eigenschaften**  >  **Kompilieren** Registerkarte **erweiterte Compilereinstellungen** festlegen.
- Versucht, Code in einer Assembly zu bearbeiten, die während des Debuggens geändert wurde und erneut geladen wurde.
- Versucht, Code in einer Assembly zu bearbeiten, die nicht geladen wurde.
- Da die neueste Version Buildfehler enthält zum Debuggen einer alten Version einer app wird gestartet.

Weitere Informationen finden Sie unter:
- [C++-bearbeiten und Fortfahren-Blog Posten](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md)
- [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md)