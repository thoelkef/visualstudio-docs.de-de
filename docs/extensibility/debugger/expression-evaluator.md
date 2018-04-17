---
title: Ausdrucksauswertung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8dd2cc4409dbdb7650454715e133fd76dda5b780
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluator"></a>Ausdrucksauswertung
Ausdrucksauswertungen (EE) untersuchen die Syntax von einer anderen Sprache zu analysieren und Auswerten von Variablen und Ausdrücke zur Laufzeit, sodass sie vom Benutzer angezeigt werden, wenn die IDE im Unterbrechungsmodus befindet.  
  
## <a name="using-expression-evaluators"></a>Ausdrucksauswertungen verwenden  
 Ausdrücke werden erstellt, mit der [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode wie folgt:  
  
1.  Implementiert die Debugging-Modul (Deutschland) das [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle.  
  
2.  Ruft das debugpaket ein `IDebugExpressionContext2` -Objekt aus einer [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle, und ruft dann die `IDebugStackFrame2::ParseText` -Methode dafür abrufen ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt.  
  
3.  Ruft die Debug-Paket die [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) Methode oder die [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) Methode, um den Wert des Ausdrucks abzurufen. `IDebugExpression2::EvaluateAsync` wird vom Befehl/Direktfenster aufgerufen. Rufen Sie alle UI-Komponenten `IDebugExpression2::EvaluateSync`.  
  
4.  Das Ergebnis der Auswertung von Ausdrücken ist ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das den Namen, Typ und Wert, der das Ergebnis der ausdrucksauswertung enthält.  
  
 Während der Auswertung von Ausdrücken benötigt die EE Informationen aus der Symbol-Anbieter-Komponente. Die Symbol-Anbieter stellt die Symbolinformationen für das Erkennen und Verstehen des analysierten Ausdrucks verwendet.  
  
 Nach Abschluss der asynchronen ausdrucksauswertung wird asynchrones Ereignis gesendet DE über die Sitzung Debug-Manager (SDM) der IDE benachrichtigt, dass die Auswertung von Ausdrücken abgeschlossen ist. Beim synchronen ausdrucksauswertung abgeschlossen ist, wird das Ergebnis der Auswertung zurückgegeben, durch den Aufruf der `IDebugExpression2::EvaluateSync` Methode.  
  
## <a name="implementation-notes"></a>Hinweise zur Implementierung  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugmodule erwarten, sprechen Sie mit der Auswertung eines Ausdrucks mithilfe der Common Language Runtime (CLR)-Schnittstellen. Folglich eine ausdrucksauswertung, die mit funktioniert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugmodule müssen die CLR unterstützen (eine vollständige Liste der alle CLR-Debugschnittstellen verwendbaren im debugref.doc, die Teil von der [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)