---
title: 'Vorgehensweise: Anwenden von Bearbeitungen im Unterbrechungsmodus mit bearbeiten und fortfahren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e26b293a5ac7326ca8f82250ec3d0da9fe96371c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069925"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Vorgehensweise: Anwenden von Bearbeitungen im Unterbrechungsmodus mit bearbeiten und fortfahren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können mit Bearbeiten und Fortfahren den Code im Unterbrechungsmodus bearbeiten und anschließend fortfahren, ohne die Codeausführung anzuhalten und erneut starten zu müssen.  
  
 Bearbeiten und Fortfahren steht in den folgenden Debugszenarios nicht zur Verfügung:  
  
- Debuggen im gemischten Modus (systemeigen/verwaltet).  
  
- SQL-Debuggen.  
  
- Debuggen einer Dr. Watson-Sicherungskopie.  
  
- Bearbeiten von Code nach einer nicht behandelten Ausnahme, wenn die Option **Aufrufliste für unbehandelte Ausnahmen entladen** nicht aktiviert ist.  
  
- Debuggen einer eingebetteten Laufzeitanwendung.  
  
- Debuggen einer Anwendung mit **Anfügen an** statt die Anwendung mit **starten** aus der **Debuggen** Menü.  
  
- Debuggen von optimiertem Code.  
  
- Debuggen von verwaltetem Code, wenn das Ziel eine 64-Bit-Anwendung ist. Wenn Sie Bearbeiten und Fortfahren verwenden möchten, müssen Sie das Ziel auf x86 festlegen. (_Projekt_**Eigenschaften**, **Kompilieren** Registerkarte **erweiterte Compilereinstellungen** festlegen.).  
  
- Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.  
  
### <a name="to-edit-code-in-break-mode"></a>So bearbeiten Sie Code im Unterbrechungsmodus  
  
1. Wechseln Sie in den Unterbrechungsmodus, indem Sie folgendermaßen vorgehen:  
  
    - Legen Sie einen Breakpoint im Code fest, wählen Sie im Menü **Debuggen** den Befehl **Debuggen starten** aus, und warten Sie, bis die Anwendung den Breakpoint erreicht.  
  
         – oder –  
  
    - Beginnen Sie mit dem Debuggen, und wählen Sie anschließend im Menü **Debuggen** den Befehl **Alle unterbrechen** aus.  
  
         – oder –  
  
    - Wenn eine Ausnahme auftritt, wählen Sie **Bearbeiten aktivieren** auf die**Ausnahmen-Assistent**.  
  
2. Nehmen Sie die gewünschten zulässigen Codeänderungen vor.  
  
     Weitere Informationen finden Sie unter [in Visual Basic zu bearbeiten und Fortfahren nicht unterstützte bearbeitet](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Bei dem Versuch, mit Bearbeiten und Fortfahren eine nicht zulässige Änderung vorzunehmen, wird die bearbeitete Stelle violett wellenförmig unterstrichen, und in der Aufgabeliste wird eine Aufgabe angezeigt. Sie können mit der Codeausführung erst fortfahren, nachdem Sie die nicht zulässige Codeänderung rückgängig gemacht haben.  
  
3. Klicken Sie im Menü **Debuggen** auf **Weiter**, um mit der Ausführung fortzufahren.  
  
     Der Code wird nun einschließlich der vorgenommenen Änderungen ausgeführt, die jetzt Teil des Projekts sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Nicht unterstützte Bearbeitungen in Visual Basic bearbeiten und fortfahren](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Bearbeiten und Fortfahren (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
