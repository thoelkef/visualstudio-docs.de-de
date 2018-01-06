---
title: Implementieren eine Ausdrucksauswertung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9f18e2e131b6baa325bd7e0b65babee4c3679ed8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-an-expression-evaluator"></a>Implementieren eine Ausdrucksauswertung
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Die Auswertung eines Ausdrucks ist ein komplexes Zusammenspiel zwischen der Debugging-Modul (DE), den Symbol-Anbieter (SP), das binderobjekt und die ausdrucksauswertung (EE) selbst. Diese vier Komponenten verbunden sind von Schnittstellen, die von einer Komponente implementiert und durch eine andere genutzt werden.  
  
 Die EE verwendet einen Ausdruck aus dem DE in Form einer Zeichenfolge analysiert und ergibt das Symbol. Die EE implementiert die folgenden Schnittstellen, die von der DE genutzt werden:  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 Die EE Ruft den Binder-Objekt, das vom DE, um den Wert der Symbole und Objekte abzurufen. Die EE nutzt die folgenden Schnittstellen, die durch die DE implementiert werden:  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 Implementiert die EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`Stellt den Mechanismus für das Ergebnis eine Auswertung von Ausdrücken, z. B. eine lokale Variable, ein primitiver Typ oder ein Objekt, um Visual Studio, klicken Sie dann die entsprechende Informationen angezeigt, die beschreibt die **"lokal"**,  **Überwachungsfenster**, oder **Direktfenster** Fenster.  
  
 Die SP wird die EE durch DE angegeben, wenn Informationen aufgefordert wird. Die SP implementiert die Schnittstellen, die Adressen und Felder, z. B. die folgenden Schnittstellen und zugehörige ableitungen beschreiben:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 Die EE verbraucht jede dieser Schnittstellen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementierungsstrategie für die Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Definiert einen dreistufigen Vorgang für der Strategie für die Implementierung der Expression Evaluator (EE).  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)