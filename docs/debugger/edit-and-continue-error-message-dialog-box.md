---
title: Bearbeiten und Fortfahren im Dialogfeld Fehlermeldung | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b521eafcc62a49f2dd2a4c327158070bdbe62ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Fehlermeldungs-Dialogfeld für "Bearbeiten und Fortfahren"
Dieses Dialogfeld wird angezeigt, wenn Sie in einer Programmiersprache Debuggen, die bearbeiten und Fortfahren unterstützt jedoch **bearbeiten und Fortfahren** ist für den Typ des von Ihnen vorgenommenen codeänderungen nicht verfügbar. Die Fehlermeldung in dem Feld enthält eine ausführlichere Erklärung. Folgende Gründe zum Anzeigen dieses Dialogfelds sind möglich:  

-   Sie haben versucht, SQL Server-Code zu bearbeiten.

-   Sie haben versucht, optimierten Code zu bearbeiten. (Möglicherweise müssen Sie aus einem Releasebuild zu einem Debugbuild zu wechseln.)

-   Sie haben versucht, Code zu bearbeiten, während der Ausführung (anstelle von während im Debugger angehalten). Wiederholen Sie den [Festlegen eines Haltepunkts](../debugger/using-breakpoints.md) und Bearbeiten von Code während angehalten.

-   Sie haben versucht, verwalteten Code zu bearbeiten, während nicht verwaltetes Debuggen aktiviert war. Bearbeiten und Fortfahren funktioniert nicht mit [Debuggen im gemischten Modus](../debugger/how-to-debug-in-mixed-mode.md).

-   Vorgenommenen eine codeänderung, die in einer Programmiersprache von bearbeiten und Fortfahren nicht unterstützt wird. Weitere Informationen finden Sie unter Themen für nicht unterstützte codeänderungen in [c#](../debugger/supported-code-changes-csharp.md), [Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md), und [C++](../debugger/supported-code-changes-cpp.md).
  
-   Sie haben versucht, Code in einem Programm zu bearbeiten, das Sie angefügt haben, statt beginnend mit der **Debuggen** Menü.  
  
-   Sie haben versucht, Code während des Debuggens eines Dr zu bearbeiten. Dr.Watson-Dumps.  
  
-   Sie haben versucht, das Bearbeiten von Code nach dem eine nicht behandelte Ausnahme aufgetreten ist und die Option "**Aufrufliste für Ausnahmefehler entladen**" wurde nicht ausgewählt.  
  
-   Sie haben versucht, Code zu bearbeiten, während Sie für eine eingebettete Laufzeitanwendung ein Debuggen durchgeführt haben.
  
-   Sie haben versucht, verwalteten Code mit .NET Framework-Version vor 4.5.1 zu bearbeiten, und das Ziel ist eine 64-Bit-Anwendung. Wenn Sie Bearbeiten und Fortfahren verwenden möchten, müssen Sie das Ziel auf x86 festlegen. (*Projektname* **Eigenschaften**, **Kompilieren** Registerkarte **erweiterte Compilereinstellungen** festlegen.).  
  
-   Sie haben versucht, Code in einer Assembly zu bearbeiten, die während des Debuggens geändert und erneut geladen wurde.  
  
-   Sie haben versucht, Code in einer Assembly zu bearbeiten, die nicht geladen wurde.  
  
-   Sie haben damit begonnen, eine alte Version der Anwendung zu debuggen (da die neue Version Buildfehler enthält).
  
## <a name="uielement-list"></a>UIElement-Liste  
 **OK**  
 Schließen Sie das Dialogfeld, und brechen Sie den unmittelbar vorausgegangenen Bearbeitungsversuch ab.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von C++-bearbeiten und Fortfahren (Blog)](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
 [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md)