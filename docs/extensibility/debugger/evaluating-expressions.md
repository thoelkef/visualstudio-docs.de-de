---
title: "Auswerten von Ausdrücken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 870469b77eb2f9fcf562602dd651c84fa71020ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="evaluating-expressions"></a>Auswerten von Ausdrücken
Ausdrücke werden von Zeichenfolgen dar, die von "Auto", Überwachung, Schnellüberwachung oder sofortige Windows übergeben, erstellt. Wenn ein Ausdruck ausgewertet wird, generiert es eine druckbare Zeichenfolge, die den Namen und Typ der Variable "oder" Argument "und" den Wert enthält. Diese Zeichenfolge wird in das entsprechende Fenster der IDE angezeigt.  
  
## <a name="implementation"></a>Implementierung  
 Ausdrücke werden ausgewertet, wenn ein Programm an einem Haltepunkt angehalten wurde. Der Ausdruck selbst wird durch dargestellt ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle, die einen analysierten Ausdruck darstellt, die für die Bindung und der Auswertung innerhalb des Kontexts des angegebenen Ausdrucks Auswertung bereit ist. Der Stapelrahmen bestimmt Evaluierungskontext Ausdruck, der durch die Implementierung der Debugging-Modul (DE) liefert die [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle.  
  
 Benutzer Zeichenfolge und ein [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle, ein Debugging-Modul (DE) erhalten eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle durch Übergeben der Benutzerzeichenfolge an die [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Methode. IDebugExpression2-Schnittstelle, die zurückgegeben enthält die analysierten Ausdrucks bereit für die Evaluierung.  
  
 Mit der `IDebugExpression2` -Schnittstelle, die DE kann den Wert des Ausdrucks durch synchrone oder asynchrone ausdrucksauswertung Abrufen mit [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Dieser Wert zusammen mit dem Namen und Typ der Variable oder eines Arguments, wird für die Anzeige der IDE gesendet. Der Wert, den Namen und den Typ von dargestellt sind ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle.  
  
 Um die Auswertung von Ausdrücken zu aktivieren, muss ein DE implementieren die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) und [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstellen. Synchrone und asynchrone Auswertung erfordern die Implementierung der [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Stapelrahmen](../../extensibility/debugger/stack-frames.md)   
 [Evaluierungskontext Ausdruck](../../extensibility/debugger/expression-evaluation-context.md)   
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)