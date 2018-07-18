---
title: Bearbeiten und Fortfahren (Visual Basic) | Microsoft Docs
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
ms.openlocfilehash: aa3b8c287129c164d8c6984ac52375d6012fbd68
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471043"
---
# <a name="edit-and-continue-visual-basic"></a>Bearbeiten und Fortfahren (Visual Basic)
Bearbeiten und Fortfahren ist ein Feature von [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Debuggen, mit dem Sie den Code ändern können, während der Unterbrechungsmodus ausgeführt wird. Nachdem Codebearbeitungen übernommen wurden, können Sie die Ausführung mit den neuen Änderungen fortsetzen und deren Auswirkung beobachten.  
  
 Sie können das Feature Bearbeiten und Fortfahren immer dann verwenden, wenn Sie sich im Unterbrechungsmodus befinden. In den Unterbrechungsmodus, der Anweisungszeiger, eine gelbe Pfeilspitze im Quellcodefenster ausgeführt verweist auf die Zeile mit der eine ausführbare Anweisung in einer Methode oder Eigenschaft Text, die weiter.

 Die Funktion "Bearbeiten und Fortfahren" unterstützt bis auf einige Ausnahmen die meisten Änderungen, die Sie möglicherweise während einer Debugsitzung vornehmen möchten. Weitere Informationen finden Sie unter [unterstützte Codeänderungen (C#- und Visual Basic)](../debugger/supported-code-changes-csharp.md).   
  
 Wenn Sie eine unberechtigte Bearbeitung vornehmen, wird die Änderung durch eine violette wellenförmige Linie gekennzeichnet, und in der Aufgabenliste wird eine Aufgabe angezeigt. Sie müssen eine unberechtigte Bearbeitung rückgängig machen, wenn Sie Bearbeiten und Fortfahren weiterhin verwenden möchten. Bestimmte unberechtigte Bearbeitungen sind möglicherweise zulässig, wenn sie außerhalb von Bearbeiten und Fortfahren durchgeführt werden. Wenn Sie die Ergebnisse einer solchen unberechtigten Bearbeitung beibehalten möchten, müssen Sie das Debuggen beenden und die Anwendung neu starten.  
  
 Bearbeiten und Fortfahren wird nur in uwp-apps für Windows 10 und X86- und X64-apps, die auf .NET Framework 4.6 abzielen unterstützt desktop oder höhere Versionen, die (das .NET Framework ist nur eine desktop-Version).

 > [!NOTE]
 > Nicht unterstützte apps und Plattformen gehören ASP.NET 5, Silverlight 5 und Windows 8.1.
  
 Bearbeiten und Fortfahren wird nicht unterstützt, beim Starten des Debuggens mit **an den Prozess anhängen**. Bearbeiten und Fortfahren wird nicht unterstützt, optimiertem Code oder gemischten verwalteten und nativen Code. Weitere Informationen finden Sie unter [unterstützte Codeänderungen (C#- und Visual Basic](../debugger/supported-code-changes-csharp.md).
  
 In den Themen zu diesem Abschnitt finden Sie weitere Informationen darüber, wie dieses Feature verwendet wird, und welche Arten von Änderungen nicht zulässig sind.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Gewusst wie: Anwenden von Bearbeitungen im Unterbrechungsmodus mithilfe von "Bearbeiten und Fortfahren"](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Erläutert, wie Codebearbeitungen im Unterbrechungsmodus vorgenommen werden.  
  
 [Unterstützte Codeänderungen (C#- und Visual Basic](../debugger/supported-code-changes-csharp.md)   
 Hier wird beschrieben, welche Arten von Bearbeitungen nicht mit der Funktion "Bearbeiten und Fortfahren" in [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] ausgeführt werden können.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md)  
 Enthält eine Liste mit Themen zu Bearbeiten und Fortfahren.