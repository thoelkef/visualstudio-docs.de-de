---
title: 'Vorgehensweise: feststellen, welche DLL Absturz des Programms | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.dll
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
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6232f86e9e9f5d59e9e109d08b75120cc90902c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Gewusst wie: Feststellen, welche DLL zum Absturz des Programms geführt hat
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
 Wenn die Anwendung während des Aufrufs einer System-DLL oder des Codes eines anderen Benutzers abstürzt, muss herausgefunden werden, welche DLL zur Zeit des Absturzes aktiv war. Wenn Sie in eine DLL außerhalb der eigenen Anwendung abgestürzt ist, können Sie identifizieren, die Ursache mithilfe der **Module** Fenster.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>So ermitteln Sie im Fenster "Module" die Stelle, die einen Absturz verursacht hat  
  
1.  Notieren Sie die Adresse, an der der Absturz stattgefunden hat.  
  
2.  Auf der **Debuggen** Menü wählen **Windows**, und klicken Sie auf **Module**.  
  
3.  In der **Module** Fenster Suchen der **Adresse** Spalte. Zur Anzeige der Spalte müssen Sie möglicherweise die Bildlaufleiste verwenden.  
  
4.  Klicken Sie auf die **Adresse** Schaltfläche am oberen Rand der Spalte, um die DLLs nach Adresse zu sortieren.  
  
5.  Durchsuchen Sie die sortierte Liste nach der DLL, in deren Adressbereich die vom Absturz betroffene Stelle zu finden ist.  
  
6.  Betrachten Sie die **Namen** und **Pfad** Spalten, um die DLL-Namen und Pfad anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md)   
 [Gewusst wie: Verwenden des Modulfensters](../debugger/how-to-use-the-modules-window.md)