---
title: Implementieren einer Ausdrucksauswertung | Microsoft-Dokumentation
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
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b32ae1580ccba207f7d5e86fc4ac48d38fec7fbf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786833"
---
# <a name="implementing-an-expression-evaluator"></a>Implementieren einer Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Die Auswertung eines Ausdrucks ist ein komplexes Zusammenspiel zwischen die Debug-Engine (DE), die Symbol-Dienstanbieter (SP), das binderobjekt und die ausdrucksauswertung (EE) selbst. Diese vier Komponenten werden durch Schnittstellen verbunden, die durch eine Komponente implementiert und von einem anderen genutzt werden.  
  
 Die EE verwendet einen Ausdruck aus der DE in Form einer Zeichenfolge und analysiert und wertet es. Die EE implementiert die folgenden Schnittstellen, die von der DE genutzt werden:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  Die EE Ruft den binderobjekt, das vom DE, um den Wert der Symbole und Objekte abzurufen. Die EE verwendet die folgenden Schnittstellen, die von der DE implementiert werden:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  Implementiert die EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` Stellt den Mechanismus bereit, beschreibt das Ergebnis der Auswertung eines Ausdrucks, z. B. eine lokale Variable, ein primitiver Typ oder ein Objekt, das Visual Studio, die die entsprechende Informationen in dann zeigt die **"lokal"**,  **Sehen Sie sich**, oder **direkt** Fenster.  
  
  Die SP wird durch die DE auf die EE gewährt, wenn Informationen aufgefordert wird. Die SP implementiert die Schnittstellen, die Adressen und Felder, z. B. die folgenden Schnittstellen und zugehörige ableitungen zu beschreiben:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  Die EE verbraucht jede dieser Schnittstellen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementierungsstrategie für die Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Definiert einen dreistufigen Prozess für die Implementierungsstrategie für die ausdrucksauswertung (EE).  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben einer CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

