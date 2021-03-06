---
title: Ausdrucks Auswertung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 423df66e8bd6bc1257a32236aa4ffbb28b80d655
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152742"
---
# <a name="expression-evaluator"></a>Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Ausdrucks Auswertung (EE) untersuchen die Syntax einer Sprache, um Variablen und Ausdrücke zur Laufzeit zu analysieren und auszuwerten, sodass Sie vom Benutzer angezeigt werden können, wenn sich die IDE im unterbrechen Modus befindet.  
  
## <a name="using-expression-evaluators"></a>Verwenden von Ausdrucks auswerteratoren  
 Ausdrücke werden [mithilfe der Methode](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) "Methode" wie folgt erstellt:  
  
1. Die Debug-Engine (de) implementiert die [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle.  
  
2. Das Debugpaket `IDebugExpressionContext2` Ruft ein Objekt aus einer [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle ab und ruft dann die- `IDebugStackFrame2::ParseText` Methode auf, um ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Objekt zu erhalten.  
  
3. Das Debugpaket Ruft die [evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) -Methode oder die [evaluateasync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) -Methode auf, um den Wert des Ausdrucks zu erhalten. `IDebugExpression2::EvaluateAsync` wird im Fenster Befehl/direkt aufgerufen. Alle anderen UI-Komponenten erfordern `IDebugExpression2::EvaluateSync` .  
  
4. Das Ergebnis der Ausdrucks Auswertung ist ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das den Namen, den Typ und den Wert des Ergebnisses der Ausdrucks Auswertung enthält.  
  
   Während der Ausdrucks Auswertung benötigt der EE Informationen von der Symbol Anbieter Komponente. Der Symbol Anbieter liefert die symbolischen Informationen, die zum Identifizieren und verstehen des analysierten Ausdrucks verwendet werden.  
  
   Wenn die asynchrone Ausdrucks Auswertung beendet ist, wird von der de durch den Sitzungs-Debug-Manager (SDM) ein asynchrones Ereignis gesendet, um die IDE zu benachrichtigen, dass die Ausdrucks Auswertung beendet ist. Wenn die Auswertung des synchronen Ausdrucks beendet ist, wird das Ergebnis der Auswertung vom aufrufsvorgang der-Methode zurückgegeben `IDebugExpression2::EvaluateSync` .  
  
## <a name="implementation-notes"></a>Hinweise zur Implementierung  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debug-engines erwarten mit der Ausdrucks Auswertung mithilfe von CLR-Schnittstellen (Common Language Runtime). Daher muss eine Ausdrucks Auswertung, die mit debuggingmodulen arbeitet, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die CLR unterstützen (eine vollständige Liste aller CLR-Debugschnittstellen finden Sie in debugref.doc, die Teil von ist [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] ).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)
