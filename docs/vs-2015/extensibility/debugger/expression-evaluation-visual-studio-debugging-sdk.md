---
title: Ausdrucks Auswertung (Visual Studio-debuggingsdk) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f2a84f01168dd01921d933a80fe052c1a6c6447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562158"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Ausdrucksauswertung (Visual Studio Debugging SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Break-Modus muss die IDE in der Lage sein, einfache Ausdrücke mit mehreren Variablen des Programms auszuwerten. Um dies zu erreichen, muss die Debug-Engine (de) einen Ausdruck analysieren und auswerten können, der in einem der Fenster der IDE eingegeben wurde.  
  
 Ausdrücke werden mithilfe der [IDebugExpressionContext2::P Ardie Text](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode erstellt und durch die resultierende [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle dargestellt.  
  
 Die **IDebugExpression2** -Schnittstelle wird von de implementiert und ruft die **evalasync** -Methode auf, um eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle an die IDE zurückzugeben, um die Ergebnisse der Ausdrucks Auswertung in der IDE anzuzeigen. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) gibt eine-Struktur zurück, die verwendet werden kann, um den Wert eines Ausdrucks in einem Überwachungsfenster oder im lokalen Fenster zu platzieren.  
  
 Das Debug-Paket oder der Session Debug Manager (SDM) ruft [IDebugExpression2:: evaluateasync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) oder [evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) auf, um eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle zu erhalten, die das Ergebnis der Auswertung darstellt. `IDebugProperty2` verfügt über Methoden, die den Namen, den Typ und den Wert des Ausdrucks zurückgeben. Diese Informationen werden in verschiedenen Debuggerfenstern angezeigt.  
  
## <a name="using-expression-evaluation"></a>Verwenden der Ausdrucks Auswertung  
 Zum Verwenden der Ausdrucks Auswertung müssen Sie die [IDebugExpressionContext2::P arltext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode und alle Methoden der [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle implementieren, wie in der folgenden Tabelle gezeigt.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet einen Ausdruck asynchron aus.|  
|[Abbruch](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone Ausdrucks Auswertung.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Wertet einen Ausdruck synchron aus.|  
  
 Die synchrone und asynchrone Auswertung erfordert die Implementierung der [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) -Methode. Bei der asynchronen Ausdrucks Auswertung ist die Implementierung von [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)erforderlich.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführungssteuerung und Zustandsauswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
