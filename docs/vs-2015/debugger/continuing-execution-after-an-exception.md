---
title: Fortsetzen der Ausführung nach einer Ausnahme | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ae74c51f0f738bc596fbe5c789011630927707c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702266"
---
# <a name="continuing-execution-after-an-exception"></a>Fortfahren mit der Ausführung nach einer Ausnahme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn die Ausführung wegen einer Ausnahme vom Debugger unterbrochen wird, wird ein Dialogfeld angezeigt. Für Visual Basic oder c# wird standardmäßig das Dialogfeld [Ausnahmen-Assistent](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) angezeigt. Für C++ wird das Dialogfeld ältere **Ausnahme** angezeigt. Wenn Sie Visual Basic oder c# verwenden, aber den Ausnahmen- **Assistenten** im Dialogfeld **Optionen** deaktiviert haben, wird das Dialogfeld **Ausnahme** angezeigt.  
  
 Wenn der **Ausnahme-Assistent** oder das Dialogfeld " **Ausnahme** " angezeigt wird, können Sie versuchen, das Problem zu beheben, das die Ausnahme verursacht hat.  
  
## <a name="managed-code"></a>Verwalteter Code  
 In verwaltetem Code kann die Ausführung nach einem Ausnahmefehler im gleichen Thread fortgesetzt werden. Der **Ausnahmen-Assistent** entlädt die aufrufsstapel an den Punkt, an dem die Ausnahme ausgelöst wurde.  
  
## <a name="native-code"></a>nativer Code  
 Bei systemeigenem C/C++ haben Sie zwei Möglichkeiten:  
  
- Sie können auf " **Abbrechen** " klicken und versuchen, das Problem zu beheben. Während Sie sich im unterschreitungsmodus befinden, können Sie die aufrufsliste entladen, indem Sie im **Fenster "** Fenster" mit der rechten Maustaste auf einen Frame klicken und im Kontextmenü die Option **zu diesem Frame** entladen auswählen. Wenn Sie das Debuggen fortsetzen, wird das Dialogfeld **Ausnahme** erneut angezeigt, wenn Sie das Problem nicht behoben haben. Andernfalls wird das Dialogfeld **Ausnahme** nicht erneut angezeigt.  
  
- Klicken Sie auf **weiter** , um die Ausführung fortzusetzen, ohne zu versuchen, das Problem zu beheben. Das Dialogfeld **Ausnahme** wird erneut angezeigt.  
  
## <a name="mixed-code"></a>Gemischter Code  
 Wenn beim Debuggen gemischten Codes (systemeigener und verwalteter Code) ein Ausnahmefehler auftritt, verhindern Einschränkungen des Betriebssystems das Entladen der Aufrufliste. Sollten Sie versuchen, die Aufrufliste über das Kontextmenü neu zu laden, erhalten Sie die Fehlermeldung, dass der Debugger beim Debuggen von gemischtem Code keine Entladung aus einer unbehandelten Ausnahme vornehmen kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)
