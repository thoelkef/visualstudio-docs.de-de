---
title: Beispiel für die Implementierung der lokalen Variablen | Microsoft-Dokumentation
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
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 23a24e36b34e1e7d5fa781153cbf5d6cd86a8df1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49219738"
---
# <a name="sample-implementation-of-locals"></a>Beispielimplementierung von lokalen Elementen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Hier ist ein Überblick darüber, wie Visual Studio die lokalen Variablen für eine Methode aus der Auswertung eines Ausdrucks (EE) erhält:  
  
1.  Ruft der Debug-Engine des (DE) für Visual Studio [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) zum Abrufen einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das alle Eigenschaften des Stapelrahmens, einschließlich der lokalen Variablen darstellt.  
  
2.  `IDebugStackFrame2::GetDebugProperty` Aufrufe [von GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) auf ein Objekt zu erhalten, die die Methode in der der Haltepunkt aufgetreten ist. Die DE stellt einen symbolanbieter ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), eine Adresse ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)), und ein Binder ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` Aufrufe [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) mit dem angegebenen `IDebugAddress` das abzurufende Objekt ein [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) , die die Methode, die mit der angegebenen Adresse darstellt.  
  
4.  Die `IDebugContainerField` Schnittstelle abgefragt wird, für die [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) Schnittstelle. Es ist dieser Schnittstelle, die der Methode "lokal" Zugriff.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` instanziiert die Klasse (namens `CFieldProperty` im Beispiel), implementiert die `IDebugProperty2` Schnittstelle, um die Methode der lokalen Variablen darstellen. Die `IDebugMethodField` Objekt befindet sich in diesem `CFieldProperty` -Objekts zusammen mit den `IDebugSymbolProvider`, `IDebugAddress` und `IDebugBinder` Objekte.  
  
6.  Wenn die `CFieldProperty` -Objekt initialisiert wird, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) aufgerufen wird die `IDebugMethodField` Objekt abrufen eine [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) Struktur, die alle anzeigbaren Informationen über die Methode selbst enthält .  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` Gibt die `CFieldProperty` als Objekt ein `IDebugProperty2` Objekt.  
  
8.  Visual Studio-Aufrufe [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) für das zurückgegebene `IDebugProperty2` Objekt mit dem Filter `guidFilterLocalsPlusArgs`. Dies gibt eine [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Objekt, das der Methode "lokal" enthält. Diese Enumeration wird durch Aufrufen von ausgefüllt [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) und [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio-Aufrufe [Weiter](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) zum Abrufen einer [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) Struktur für jedes lokale. Diese Struktur enthält einen Zeiger auf ein `IDebugProperty2` Schnittstelle für eine lokale.  
  
10. Visual Studio-Aufrufe [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) für jede lokale zum Abrufen des lokalen Namen, Wert und Typ. Dies sind die Informationen, die in angezeigt wird der **"lokal"** Fenster.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren von GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Beschreibt eine Implementierung von [von GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Auflisten von lokalen Elementen](../../extensibility/debugger/enumerating-locals.md)  
 Beschreibt, wie die Debug-Engine (DE) zum Auflisten von lokalen Variablen oder Argumenten aufruft.  
  
 [Abrufen von lokalen Eigenschaften](../../extensibility/debugger/getting-local-properties.md)  
 Beschreibt, wie die DE erhalten den Namen, Typ und Wert, der eine oder mehrere lokale Variablen aufruft.  
  
 [Abrufen von lokalen Werten](../../extensibility/debugger/getting-local-values.md)  
 Erläutert das Abrufen des Werts der lokalen, müssen Sie die Dienste der ein binderobjekt, das durch den Auswertungskontext angegeben.  
  
 [Auswerten von lokalen Elementen](../../extensibility/debugger/evaluating-locals.md)  
 Erläutert, wie lokale Variablen ausgewertet werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Auswertungskontext](../../extensibility/debugger/evaluation-context.md)  
 Übergibt die Argumente, die übergeben werden, wenn die DE die ausdrucksauswertung (EE) aufruft.  
  
 [MyCEE-Beispiel](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Zeigt eine Implementierungsansatz zum Erstellen von einer ausdrucksauswertung für die Sprache MyC an.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)

