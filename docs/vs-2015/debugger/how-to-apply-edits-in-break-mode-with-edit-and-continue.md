---
title: 'Vorgehensweise: Anwenden von Bearbeitungen im Unterbrechungsmodus mit bearbeiten und fortfahren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 5f6024d0c00e492110d7d34172cf225e4712f213
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807497"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Gewusst wie: Anwenden von Bearbeitungen im Unterbrechungsmodus mithilfe von "Bearbeiten und Fortfahren"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können mit Bearbeiten und Fortfahren den Code im Unterbrechungsmodus bearbeiten und anschließend fortfahren, ohne die Codeausführung anzuhalten und erneut starten zu müssen.  
  
 Bearbeiten und Fortfahren steht in den folgenden Debugszenarios nicht zur Verfügung:  
  
-   Debuggen im gemischten Modus (systemeigen/verwaltet).  
  
-   SQL-Debuggen.  
  
-   Debuggen eines Dr.Watson-Dumps.  
  
-   Bearbeiten von Code nach einer nicht behandelten Ausnahme, wenn die Option **Aufrufliste für unbehandelte Ausnahmen entladen** nicht aktiviert ist.  
  
-   Debuggen einer eingebetteten Laufzeitanwendung.  
  
-   Debuggen einer Anwendung mit **Anfügen an** statt die Anwendung mit **starten** aus der **Debuggen** Menü.  
  
-   Debuggen von optimiertem Code.  
  
-   Debuggen von verwaltetem Code, wenn das Ziel eine 64-Bit-Anwendung ist. Wenn Sie Bearbeiten und Fortfahren verwenden möchten, müssen Sie das Ziel auf x86 festlegen. (_Projekt_**Eigenschaften**, **Kompilieren** Registerkarte **erweiterte Compilereinstellungen** festlegen.).  
  
-   Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.  
  
### <a name="to-edit-code-in-break-mode"></a>So bearbeiten Sie Code im Unterbrechungsmodus  
  
1.  Wechseln Sie in den Unterbrechungsmodus, indem Sie folgendermaßen vorgehen:  
  
    -   Legen Sie einen Haltepunkt im Code, und wählen Sie dann **Debuggen starten** aus der **Debuggen** Menü und warten Sie, für die Anwendung auf den Haltepunkt trifft.  
  
         – oder –  
  
    -   Mit dem Debuggen beginnen, und wählen Sie dann **alle unterbrechen** aus der **Debuggen** Menü.  
  
         – oder –  
  
    -   Wenn eine Ausnahme auftritt, wählen Sie **Bearbeiten aktivieren** auf die**Ausnahmen-Assistent**.  
  
2.  Nehmen Sie die gewünschten zulässigen Codeänderungen vor.  
  
     Weitere Informationen finden Sie unter [in Visual Basic zu bearbeiten und Fortfahren nicht unterstützte bearbeitet](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Bei dem Versuch, mit Bearbeiten und Fortfahren eine nicht zulässige Änderung vorzunehmen, wird die bearbeitete Stelle violett wellenförmig unterstrichen, und in der Aufgabeliste wird eine Aufgabe angezeigt. Sie können mit der Codeausführung erst fortfahren, nachdem Sie die nicht zulässige Codeänderung rückgängig gemacht haben.  
  
3.  Auf der **Debuggen** Menü klicken Sie auf **Weiter** um die Ausführung fortzusetzen.  
  
     Der Code wird nun einschließlich der vorgenommenen Änderungen ausgeführt, die jetzt Teil des Projekts sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Nicht unterstützte Bearbeitungen in Visual Basic bearbeiten und fortfahren](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Bearbeiten und Fortfahren (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)



