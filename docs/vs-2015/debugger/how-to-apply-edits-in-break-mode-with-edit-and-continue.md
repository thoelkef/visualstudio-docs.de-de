---
title: 'Vorgehensweise: Anwenden von Bearbeitungen im Break-Modus mit "Bearbeiten und Fortfahren" | Microsoft-Dokumentation'
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
ms.openlocfilehash: 5c04dc0ae6e5272d2544ad7436fa7ca516c9a022
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840958"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Gewusst wie: Anwenden von Bearbeitungen im Unterbrechungsmodus mithilfe von "Bearbeiten und Fortfahren"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können mit Bearbeiten und Fortfahren den Code im Unterbrechungsmodus bearbeiten und anschließend fortfahren, ohne die Codeausführung anzuhalten und erneut starten zu müssen.  
  
 Bearbeiten und Fortfahren steht in den folgenden Debugszenarios nicht zur Verfügung:  
  
- Debuggen im gemischten Modus (systemeigen/verwaltet).  
  
- SQL-Debuggen.  
  
- Debuggen einer Dr. Watson-Sicherungskopie.  
  
- Bearbeiten von Code nach einer nicht behandelten Ausnahme, wenn die Option **Aufrufliste für unbehandelte Ausnahmen entladen** nicht aktiviert ist.  
  
- Debuggen einer eingebetteten Laufzeitanwendung.  
  
- Debuggen einer Anwendung mit **Anfügen an,** anstatt die Anwendung mit **Start** im Menü **Debuggen** ausführen.  
  
- Debuggen von optimiertem Code.  
  
- Debuggen von verwaltetem Code, wenn das Ziel eine 64-Bit-Anwendung ist. Wenn Sie Bearbeiten und Fortfahren verwenden möchten, müssen Sie das Ziel auf x86 festlegen. (_Projekt_**Eigenschaften**, Registerkarte **Kompilieren** , **Erweiterte Compilereinstellung** .).  
  
- Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.  
  
### <a name="to-edit-code-in-break-mode"></a>So bearbeiten Sie Code im Unterbrechungsmodus  
  
1. Wechseln Sie in den Unterbrechungsmodus, indem Sie folgendermaßen vorgehen:  
  
    - Legen Sie einen Breakpoint im Code fest, wählen Sie im Menü **Debuggen** den Befehl **Debuggen starten** aus, und warten Sie, bis die Anwendung den Breakpoint erreicht.  
  
         – oder –  
  
    - Beginnen Sie mit dem Debuggen, und wählen Sie anschließend im Menü **Debuggen** den Befehl **Alle unterbrechen** aus.  
  
         – oder –  
  
    - Wenn eine Ausnahme auftritt, wählen Sie im Ausnahmen-**Assistenten**die Option **Bearbeitung aktivieren** aus.  
  
2. Nehmen Sie die gewünschten zulässigen Codeänderungen vor.  
  
     Weitere Informationen finden Sie unter [nicht unterstützte Bearbeitungen in Visual Basic bearbeiten und Fortfahren](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    > Bei dem Versuch, mit Bearbeiten und Fortfahren eine nicht zulässige Änderung vorzunehmen, wird die bearbeitete Stelle violett wellenförmig unterstrichen, und in der Aufgabeliste wird eine Aufgabe angezeigt. Sie können mit der Codeausführung erst fortfahren, nachdem Sie die nicht zulässige Codeänderung rückgängig gemacht haben.  
  
3. Klicken Sie im Menü **Debuggen** auf **Weiter**, um mit der Ausführung fortzufahren.  
  
     Der Code wird nun einschließlich der vorgenommenen Änderungen ausgeführt, die jetzt Teil des Projekts sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Nicht unterstützte Bearbeitungen in Visual Basic bearbeiten und fortfahren](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Bearbeiten und Fortfahren (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
