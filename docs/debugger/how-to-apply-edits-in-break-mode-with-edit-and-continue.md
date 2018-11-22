---
title: 'Vorgehensweise: Anwenden von Bearbeitungen im Unterbrechungsmodus mit bearbeiten und fortfahren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f45b2a64e7602d038a12f436019a8f99e352aa26
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257071"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Vorgehensweise: Anwenden von Bearbeitungen im Unterbrechungsmodus mit bearbeiten und Fortfahren (Visual Basic)
Sie können mit Bearbeiten und Fortfahren den Code im Unterbrechungsmodus bearbeiten und anschließend fortfahren, ohne die Codeausführung anzuhalten und erneut starten zu müssen.  
  
Einschränkungen zur Verwendung von während des Debuggens bearbeiten und fortfahren, finden Sie unter [Supported Code Changes (C# und Visual Basic](../debugger/supported-code-changes-csharp.md)]
  
### <a name="to-edit-code-in-break-mode"></a>So bearbeiten Sie Code im Unterbrechungsmodus  
  
1.  Wechseln Sie in den Unterbrechungsmodus, indem Sie folgendermaßen vorgehen:  
  
    -   Legen Sie einen Haltepunkt im Code, und wählen Sie dann **Debuggen starten** aus der **Debuggen** Menü und warten Sie, für die Anwendung auf den Haltepunkt trifft.  
  
         - oder -   
  
    -   Mit dem Debuggen beginnen, und wählen Sie dann **alle unterbrechen** aus der **Debuggen** Menü.  
  
         - oder -   
  
    -   Wenn eine Ausnahme auftritt, wählen Sie **Bearbeiten aktivieren** auf die **Ausnahmen-Assistent**.  
  
2.  Stellen Sie alle gewünschten und unterstützte codeänderungen.  
  
     Weitere Informationen finden Sie unter [Supported Code Changes (C# und Visual Basic](../debugger/supported-code-changes-csharp.md).  
  
    > [!NOTE]
    >  Bei dem Versuch, mit Bearbeiten und Fortfahren eine nicht zulässige Änderung vorzunehmen, wird die bearbeitete Stelle violett wellenförmig unterstrichen, und in der Aufgabeliste wird eine Aufgabe angezeigt. Sie können mit der Codeausführung erst fortfahren, nachdem Sie die nicht zulässige Codeänderung rückgängig gemacht haben.  
  
3.  Auf der **Debuggen** Menü klicken Sie auf **Weiter** um die Ausführung fortzusetzen.  
  
     Der Code wird nun einschließlich der vorgenommenen Änderungen ausgeführt, die jetzt Teil des Projekts sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützte Codeänderungen (C# und Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [Bearbeiten und Fortfahren (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)