---
title: Anzeigen von "lokal" | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03a3f08498e8b046b02defd32083677b7f39e7e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108429"
---
# <a name="displaying-locals"></a>Anzeigen von "lokal"
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ausführung immer findet innerhalb des Kontexts einer Methode, auch bekannt als die enthaltende Methode oder die aktuelle Methode. Wenn die Ausführung angehalten wird, ruft Visual Studio die Debugging-Modul (DE) zum Abrufen einer Liste von lokalen Variablen und Argumente, die zusammen die "lokal", der die Methode aufgerufen. Visual Studio zeigt an, diese "lokal" und deren Werte in der **"lokal"** Fenster.  
  
 Zum Anzeigen von "lokal" die DE Ruft die [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) Methode der EE und übergibt ein Evaluierungskontext wird, die, ein Symbol-Anbieter (SP), die aktuelle Ausführung-Adresse und ein binderobjekt. Weitere Informationen finden Sie unter [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md). Wenn der Aufruf erfolgreich ist, die `IDebugExpressionEvaluator::GetMethodProperty` Methode gibt ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das die Methode darstellt, die die aktuelle Ausführung Adresse enthält.  
  
 Ruft die DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) zum Abrufen einer [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) Objekt, das gefiltert, dass nur "lokal" zurückgegeben wird und aufgelistet, um eine Liste der zu erzeugen [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)Strukturen. Jede Struktur enthält die Namen, Typ und Wert eines lokalen. Der Typ und Wert werden als geeignet für die Anzeige formatierte Zeichenfolgen gespeichert. Der Name, Typ und Wert sind in der Regel zusammen in einer einzigen Codezeile angezeigt der **"lokal"** Fenster.  
  
> [!NOTE]
>  Die **Schnellüberwachung** und **Überwachen** Windows sich ebenfalls Variablen mit dem gleichen Format von Namen, Wert und Typ anzeigen. Diese Werte werden jedoch durch den Aufruf abgerufen [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) anstelle von `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Beispielimplementierung von lokalen Elementen](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Verwendet Beispiele, um den Prozess der Implementierung von "lokal" in Einzelschritten.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Auswertungskontext](../../extensibility/debugger/evaluation-context.md)  
 Erläutert, dass die Debugging-Modul (DE) die ausdrucksauswertung (EE) aufgerufen wird, drei Argumente übergeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)