---
title: Bearbeiten und Fortfahren (Visual Basic) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 290216d9baa2692b1cb05741f3b1afc22c74988c
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307660"
---
# <a name="edit-and-continue-visual-basic"></a>Bearbeiten und Fortfahren (Visual Basic)
Bearbeiten und Fortfahren ist eine Funktion von [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)]-Debuggen, mit dem Sie den Code ändern können, während der Unterbrechungsmodus ausgeführt wird. Nachdem Codebearbeitungen übernommen wurden, können Sie die Ausführung mit den neuen Änderungen fortsetzen und deren Auswirkung beobachten.  
  
 Sie können die Funktion Bearbeiten und Fortfahren immer dann verwenden, wenn Sie sich im Unterbrechungsmodus befinden. Im Unterbrechungsmodus befindet, den Anweisungszeiger, eine gelbe Pfeilspitze im Quellcodefenster ausgeführt, zeigt auf die Zeile mit der eine ausführbare Anweisung in einer Methode oder Eigenschaft Text, die weiter.

 Die Funktion "Bearbeiten und Fortfahren" unterstützt bis auf einige Ausnahmen die meisten Änderungen, die Sie möglicherweise während einer Debugsitzung vornehmen möchten. Weitere Informationen finden Sie unter [Supported Code Changes (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).   
  
 Wenn Sie eine unberechtigte Bearbeitung vornehmen, wird die Änderung durch eine violette wellenförmige Linie gekennzeichnet, und in der Aufgabenliste wird eine Aufgabe angezeigt. Sie müssen eine unberechtigte Bearbeitung rückgängig machen, wenn Sie Bearbeiten und Fortfahren weiterhin verwenden möchten. Bestimmte unberechtigte Bearbeitungen sind möglicherweise zulässig, wenn sie außerhalb von Bearbeiten und Fortfahren durchgeführt werden. Wenn Sie die Ergebnisse einer solchen unberechtigten Bearbeitung beibehalten möchten, müssen Sie das Debuggen beenden und die Anwendung neu starten.  
  
 Bearbeiten und Fortfahren wird unterstützt, in X86- und X64 apps, die auf .NET Framework 4.6 abzielen und UWP-apps für Windows 10 desktop oder höhere Versionen, die (das .NET Framework ist nur eine desktop-Version).

 > [!NOTE]
 > Nicht unterstützte Anwendungen und Plattformen gehören ASP.NET 5, Silverlight 5 und Windows 8.1.
  
 Bearbeiten und Fortfahren wird nicht unterstützt, wenn Sie das Debuggen mit **An den Prozess anhängen** beginnen. Bearbeiten und Fortfahren wird nicht unterstützt, von optimiertem Code oder gemischten verwalteten und systemeigenen Code. Weitere Informationen finden Sie unter [Supported Code Changes (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).
  
 In den Themen zu diesem Abschnitt finden Sie weitere Informationen darüber, wie diese Funktion verwendet wird, und welche Arten von Änderungen nicht zulässig sind.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorgehensweise: Anwenden von Bearbeitungen im Unterbrechungsmodus mithilfe von „Bearbeiten und Fortfahren“](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Erläutert, wie Codebearbeitungen im Unterbrechungsmodus vorgenommen werden.  
  
 [Unterstützte Codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md)   
 Hier wird beschrieben, welche Arten von Bearbeitungen nicht mit der Funktion "Bearbeiten und Fortfahren" in [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] ausgeführt werden können.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md)  
 Enthält eine Liste mit Themen zu Bearbeiten und Fortfahren.
