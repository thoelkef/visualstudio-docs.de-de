---
title: Implementierung von "lokal"-Beispiel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56ac92989abe929884ac029e3b9c9c7dafad5fd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130478"
---
# <a name="sample-implementation-of-locals"></a>Beispielimplementierung von "lokal"
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Hier wird ein Überblick darüber, wie Visual Studio die "lokal" für eine Methode aus der Auswertung eines Ausdrucks (EE) erhält:  
  
1.  Visual Studio ruft das Debuggen Modul (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) zum Abrufen einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das alle Eigenschaften des Stapelrahmens, einschließlich der "lokal" darstellt.  
  
2.  `IDebugStackFrame2::GetDebugProperty` Aufrufe [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) , ein Objekt abzurufen, die die Methode beschreibt, anhand derer der Haltepunkt aufgetreten ist. Die DE bereitstellt, einen Symbol-Anbieter ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), eine Adresse ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)), und ein Binder ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` Aufrufe [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) mit dem angegebenen `IDebugAddress` abzurufenden Objekts ein [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) , das mit der angegebenen Adresse Methode darstellt.  
  
4.  Die `IDebugContainerField` Schnittstelle wird abgefragt, für die [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) Schnittstelle. Diese Schnittstelle, die Zugriff auf die Methode "lokal" möglich ist.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` instanziiert eine Klasse (aufgerufen `CFieldProperty` im Beispiel), implementiert die `IDebugProperty2` Schnittstelle, um die Methode "lokal" darzustellen. Die `IDebugMethodField` Objekt befindet sich in diesem `CFieldProperty` -Objekts zusammen mit den `IDebugSymbolProvider`, `IDebugAddress` und `IDebugBinder` Objekte.  
  
6.  Wenn die `CFieldProperty` -Objekt initialisiert wird, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) für aufgerufen wird die `IDebugMethodField` Objekt abrufen eine [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) Struktur, die alle darstellbaren Informationen über die Methode selbst enthält .  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` Gibt die `CFieldProperty` -Objekt als ein `IDebugProperty2` Objekt.  
  
8.  Visual Studio-Aufrufe [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) für das zurückgegebene `IDebugProperty2` Objekt mit dem Filter `guidFilterLocalsPlusArgs`. Dies gibt eine [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) Objekt, das die Methode "lokal" enthält. Diese Enumeration wird durch Aufrufe von ausgefüllt [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) und [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio-Aufrufe [Weiter](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) zum Abrufen einer [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) Struktur für jedes lokale. Diese Struktur enthält einen Zeiger auf eine `IDebugProperty2` Schnittstelle für eine lokale.  
  
10. Visual Studio-Aufrufe [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) für jede lokal auf des lokalen Namen, Wert und Typ abzurufen. Dies sind die Informationen, die in angezeigt wird der **"lokal"** Fenster.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren von GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Beschreibt eine Implementierung von [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Auflisten von lokalen Elementen](../../extensibility/debugger/enumerating-locals.md)  
 Beschreibt, wie die Debugging-Modul (DE) lokale Variablen oder Argumente aufgezählt aufruft.  
  
 [Abrufen von lokalen Eigenschaften](../../extensibility/debugger/getting-local-properties.md)  
 Beschreibt, wie die DE einen Aufruf zum Abrufen von Name, Typ und Wert, der eine oder mehrere "lokal" bietet.  
  
 [Abrufen von lokalen Werten](../../extensibility/debugger/getting-local-values.md)  
 Erläutert das Abrufen des Werts der lokalen, der die Dienste der ein binderobjekt, das vom Evaluierungskontext erforderlich ist.  
  
 [Auswerten von lokalen Elementen](../../extensibility/debugger/evaluating-locals.md)  
 Erläutert, wie "lokal" ausgewertet werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Auswertungskontext](../../extensibility/debugger/evaluation-context.md)  
 Stellt die Argumente, die übergeben werden, wenn die DE die ausdrucksauswertung (EE) aufruft.  
  
 [MyCEE-Beispiel](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Wird eine Implementierungsansatz für das Erstellen einer ausdrucksauswertung für die Sprache MyC veranschaulicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)