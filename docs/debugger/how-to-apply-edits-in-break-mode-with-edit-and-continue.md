---
title: 'Vorgehensweise: Anwenden von Bearbeitungen im Unterbrechungsmodus mit bearbeiten und fortfahren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e925ab0f989a0d817ce7aaa7ca1d15171555f27e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Gewusst wie: Anwenden von Bearbeitungen im Unterbrechungsmodus mithilfe von "Bearbeiten und Fortfahren"
Sie können mit Bearbeiten und Fortfahren den Code im Unterbrechungsmodus bearbeiten und anschließend fortfahren, ohne die Codeausführung anzuhalten und erneut starten zu müssen.  
  
Einschränkungen für bearbeiten und Fortfahren während des Debuggens verwenden, finden Sie unter [unterstützte Codeänderungen (C#- und Visual Basic](../debugger/supported-code-changes-csharp.md)]
  
### <a name="to-edit-code-in-break-mode"></a>So bearbeiten Sie Code im Unterbrechungsmodus  
  
1.  Wechseln Sie in den Unterbrechungsmodus, indem Sie folgendermaßen vorgehen:  
  
    -   Legen Sie einen Haltepunkt im Code aus, und wählen Sie dann **Debuggen** aus der **Debuggen** Menü- und warten Sie die Anwendung auf den Haltepunkt trifft.  
  
         - oder -   
  
    -   Mit dem Debuggen beginnen, und wählen Sie dann **alle unterbrechen** aus der **Debuggen** Menü.  
  
         - oder -   
  
    -   Wenn eine Ausnahme auftritt, wählen Sie **Bearbeiten aktivieren** auf die**Ausnahmen-Assistent**.  
  
2.  Stellen Sie alle gewünschten und unterstützte codeänderungen.  
  
     Weitere Informationen finden Sie unter [unterstützte Codeänderungen (C#- und Visual Basic](../debugger/supported-code-changes-csharp.md).  
  
    > [!NOTE]
    >  Bei dem Versuch, mit Bearbeiten und Fortfahren eine nicht zulässige Änderung vorzunehmen, wird die bearbeitete Stelle violett wellenförmig unterstrichen, und in der Aufgabeliste wird eine Aufgabe angezeigt. Sie können mit der Codeausführung erst fortfahren, nachdem Sie die nicht zulässige Codeänderung rückgängig gemacht haben.  
  
3.  Auf der **Debuggen** Menü klicken Sie auf **Fortfahren** um die Ausführung fortzusetzen.  
  
     Der Code wird nun einschließlich der vorgenommenen Änderungen ausgeführt, die jetzt Teil des Projekts sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützte Codeänderungen (C#- und Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [Bearbeiten und Fortfahren (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)