---
title: 'Vorgehensweise: Feststellen, welche DLL Absturz des Programms | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7726c7fff2f747fcde3fe62bcdcc0866b375728d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879120"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Vorgehensweise: Feststellen, welche DLL Absturz des Programms (C#, C++, Visual Basic F#)
  
 Wenn die Anwendung während des Aufrufs einer System-DLL oder des Codes eines anderen Benutzers abstürzt, muss herausgefunden werden, welche DLL zur Zeit des Absturzes aktiv war. Wenn Sie feststellen, dass eine DLL außerhalb der eigenen Anwendung abgestürzt ist, kann die Ursache mithilfe des Fensters **Module** ermittelt werden.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>So ermitteln Sie im Fenster "Module" die Stelle, die einen Absturz verursacht hat  
  
1.  Notieren Sie die Adresse, an der der Absturz stattgefunden hat.

    Wenn die Adresse in der Fehlermeldung nicht angezeigt wird, müssen Sie alternative Methoden zu verwenden, um die DLL zu identifizieren. Wenn Sie eine System-DLL vermuten, können Sie [Laden von Symbolen](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) von den Microsoft-Symbolservern beim Debuggen. Andernfalls müssen möglicherweise [Erstellen einer Dumpdatei](../debugger/using-dump-files.md) mit heap Informationen stattdessen. Verschiedene [Tools](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) stehen für die debugdumpdateien erstellt.
  
2.  Wählen Sie im Menü **Debuggen** die Option **Fenster** aus, und klicken Sie auf **Module**.  
  
3.  Suchen Sie im Fenster **Module** die Spalte **Adresse**. Zur Anzeige der Spalte müssen Sie möglicherweise die Bildlaufleiste verwenden.  
  
4.  Klicken Sie im oberen Spaltenbereich auf die Schaltfläche **Adresse**, um die DLLs der Adresse nach zu sortieren.  
  
5.  Durchsuchen Sie die sortierte Liste nach der DLL, in deren Adressbereich die vom Absturz betroffene Stelle zu finden ist.  
  
6.  Namen und Pfad der DLL finden Sie in der Spalte **Name** bzw. **Pfad**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md)   
 [Vorgehensweise: Verwenden des Modulfensters](../debugger/how-to-use-the-modules-window.md)