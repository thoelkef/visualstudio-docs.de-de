---
title: 'Vorgehensweise: feststellen, welche DLL Absturz des Programms | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 350cd8a78780eb8ddb2a197ed1e8920fda23bbf3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Gewusst wie: Feststellen, welche DLL zum Absturz des Programms geführt hat
  
 Wenn die Anwendung während des Aufrufs einer System-DLL oder des Codes eines anderen Benutzers abstürzt, muss herausgefunden werden, welche DLL zur Zeit des Absturzes aktiv war. Wenn Sie in eine DLL außerhalb der eigenen Anwendung abgestürzt ist, können Sie identifizieren, die Ursache mithilfe der **Module** Fenster.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>So ermitteln Sie im Fenster "Module" die Stelle, die einen Absturz verursacht hat  
  
1.  Notieren Sie die Adresse, an der der Absturz stattgefunden hat.

    Wenn die Adresse in der Fehlermeldung nicht angezeigt wird, müssen Sie alternative Methoden verwenden, um die DLL zu identifizieren. Wenn Sie eine System-DLL den Verdacht haben, können Sie [Laden von Symbolen](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) von den Microsoft-Symbolservern beim Debuggen. Andernfalls, Sie müssen möglicherweise [Erstellen einer Dumpdatei](../debugger/using-dump-files.md) mit heap Informationen stattdessen. Verschiedene [Tools](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) zum Erstellen von Dumpdateien verfügbar sind.
  
2.  Auf der **Debuggen** Menü wählen **Windows**, und klicken Sie auf **Module**.  
  
3.  In der **Module** Fenster Suchen der **Adresse** Spalte. Zur Anzeige der Spalte müssen Sie möglicherweise die Bildlaufleiste verwenden.  
  
4.  Klicken Sie auf die **Adresse** Schaltfläche am oberen Rand der Spalte, um die DLLs nach Adresse zu sortieren.  
  
5.  Durchsuchen Sie die sortierte Liste nach der DLL, in deren Adressbereich die vom Absturz betroffene Stelle zu finden ist.  
  
6.  Betrachten Sie die **Namen** und **Pfad** Spalten, um die DLL-Namen und Pfad anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md)   
 [Gewusst wie: Verwenden des Modulfensters](../debugger/how-to-use-the-modules-window.md)