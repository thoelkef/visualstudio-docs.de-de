---
title: Ausdrucksauswertung im Unterbrechungsmodus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5b307dead1d2fb193f7d34b28ef4eaec11c6dad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728995"
---
# <a name="expression-evaluation-in-break-mode"></a>Ausdrucksauswertung im Unterbrechungsmodus
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird beschrieben, den Prozess, der auftritt, wenn der Debugger im Unterbrechungsmodus befindet und muss die Auswertung von Ausdrücken durchzuführen.  
  
## <a name="expression-evaluation-process"></a>Ausdruck Evaluierungsprozesses  
 Dies sind die grundlegenden Schritte bei der Auswertung eines Ausdrucks:  
  
1.  Ruft die Sitzungs-Debug-Manager (SDM) [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) beim Abrufen einer Ausdruck-Kontext-Schnittstelle [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Klicken Sie dann aufruft, das SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) mit der Zeichenfolge analysiert werden.  
  
3.  Wenn ParseText nicht S_OK zurückgibt, wird die Ursache des Fehlers zurückgegeben.  
  
     – andernfalls:  
  
     Wenn ParseText S_OK zurückgibt, das SDM kann, rufen Sie entweder [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) um einen endgültigen Wert aus den analysierten Ausdruck abzurufen.  
  
    -   Stellt die Verwendung von `IDebugExpression2::EvaluateSync`, die bestimmten Rückruf-Schnittstelle wird verwendet, um der Auswertung des laufenden Prozesses zu kommunizieren. Der endgültige Wert wird zurückgegeben, eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle.  
  
    -   Stellt die Verwendung von `IDebugExpression2::EvaluateAsync`, die bestimmten Rückruf-Schnittstelle wird verwendet, um der Auswertung des laufenden Prozesses zu kommunizieren. Nachdem die Auswertung abgeschlossen ist, sendet EvaluateAsync ein [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) Schnittstelle über den Rückruf. Mit dieser Ereignisschnittstelle, die der endgültige Wert erzielt werden, mit [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)

