---
title: Ausdrucksauswertung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8856284869a256f9be08931b36db644621a3202d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513966"
---
# <a name="expression-evaluator"></a>Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Ausdrucksauswertung](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluator).  
  
Ausdrucksauswertungen (EE) überprüfen die Syntax einer Sprache zum Analysieren und Auswerten von Variablen und Ausdrücke zur Laufzeit, sodass sie vom Benutzer angezeigt werden, wenn die IDE im Unterbrechungsmodus befindet.  
  
## <a name="using-expression-evaluators"></a>Ausdrucksauswertungen verwenden  
 Ausdrücke werden erstellt, mit der [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode wie folgt:  
  
1.  Die Debug-Engine (DE) implementiert die [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle.  
  
2.  Ruft ab, das debugpaket ein `IDebugExpressionContext2` -Objekt aus einer [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle und ruft dann die `IDebugStackFrame2::ParseText` Methode darauf, um die erste ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt.  
  
3.  Ruft die Debug-Paket der [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) Methode oder der [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) Methode, um den Wert des Ausdrucks zu erhalten. `IDebugExpression2::EvaluateAsync` wird vom Befehl/Direktfenster aufgerufen. Alle anderen UI-Komponenten aufrufen `IDebugExpression2::EvaluateSync`.  
  
4.  Das Ergebnis der Auswertung des Ausdrucks ist ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das die Namen, Typ und Wert das Ergebnis der Auswertung des Ausdrucks enthält.  
  
 Beim Auswerten des Ausdrucks erfordert die EE Informationen aus der Symbol-Anbieter-Komponente. Der symbolanbieter stellt die symbolische Informationen zum Identifizieren und Grundlegendes zu den analysierten Ausdruck.  
  
 Wenn asynchrone ausdrucksauswertung abgeschlossen ist, wird ein asynchrones Ereignis per die DE über die sitzungsbasierter Debug-Manager (SDM) der IDE benachrichtigt, dass die Auswertung des Ausdrucks abgeschlossen ist. Bei synchronen ausdrucksauswertung abgeschlossen ist, wird das Ergebnis der Auswertung zurückgegeben, durch den Aufruf der `IDebugExpression2::EvaluateSync` Methode.  
  
## <a name="implementation-notes"></a>Hinweise zur Implementierung  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debug-Engines für die Kommunikation mit der Auswertung eines Ausdrucks mithilfe der Common Language Runtime (CLR)-Schnittstellen zu erwarten. Daher eine ausdrucksauswertung, die funktioniert mit den [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debug-Engines müssen die CLR unterstützt (eine vollständige Liste der alle CLR-Debugschnittstellen befinden sich debugref.doc, gehört der der [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)]).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)

