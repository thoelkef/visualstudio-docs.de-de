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
ms.openlocfilehash: 37a285a48ec58ddeaeae55601565c155d0455402
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958627"
---
# <a name="continuing-execution-after-an-exception"></a>Fortfahren mit der Ausführung nach einer Ausnahme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn die Ausführung wegen einer Ausnahme vom Debugger unterbrochen wird, wird ein Dialogfeld angezeigt. Für Visual Basic oder C#-, sehen Sie die [Ausnahmen-Assistent](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) Dialogfeld, in der Standardeinstellung. Für C++, sehen Sie die ältere **Ausnahme** Dialogfeld. Wenn Sie Visual Basic oder c# verwenden, aber deaktiviert haben die **Ausnahmen-Assistent** in die **Optionen** im Dialogfeld wird Ihnen die **Ausnahme** im Dialogfeld.  
  
 Wenn die **Ausnahmen-Assistent** oder **Ausnahme** Dialogfeld angezeigt wird, können Sie versuchen, das Problem zu beheben, die die Ausnahme verursacht hat.  
  
## <a name="managed-code"></a>Verwalteter Code  
 In verwaltetem Code kann die Ausführung nach einem Ausnahmefehler im gleichen Thread fortgesetzt werden. Die **Ausnahmen-Assistent** entlädt die Aufrufliste zu dem Punkt, in dem die Ausnahme ausgelöst wurde.  
  
## <a name="native-code"></a>nativer Code  
 Bei systemeigenem C/C++ haben Sie zwei Möglichkeiten:  
  
-   Klicken Sie auf **unterbrechen** und versuchen Sie es, um das Problem zu beheben. Während Sie sich im Unterbrechungsmodus befinden, können Sie die Aufrufliste entladen, indem Sie mit der rechten Maustaste auf einen Rahmen in der **Aufrufliste** Fenster, und wählen **Entladung an diesen Rahmen** im Kontextmenü auf. Wenn Sie fortfahren, Debuggen, die **Ausnahme** Dialogfeld wird erneut angezeigt, wenn Sie das Problem nicht behoben haben. Andernfalls die **Ausnahme** im Dialogfeld werden nicht erneut angezeigt.  
  
-   Klicken Sie auf **Weiter** um die Ausführung fortzusetzen, ohne zu versuchen, das Problem zu beheben. Die **Ausnahme** Dialogfeld wird erneut angezeigt.  
  
## <a name="mixed-code"></a>Gemischter Code  
 Wenn beim Debuggen gemischten Codes (systemeigener und verwalteter Code) ein Ausnahmefehler auftritt, verhindern Einschränkungen des Betriebssystems das Entladen der Aufrufliste. Sollten Sie versuchen, die Aufrufliste über das Kontextmenü neu zu laden, erhalten Sie die Fehlermeldung, dass der Debugger beim Debuggen von gemischtem Code keine Entladung aus einer unbehandelten Ausnahme vornehmen kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)
