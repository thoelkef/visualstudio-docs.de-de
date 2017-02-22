---
title: "Beispielimplementierung von lokalen Variablen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen lokale Variablen [Debugging-SDK]"
  - "Auswertung von Ausdrücken, lokale Variablen"
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Beispielimplementierung von lokalen Variablen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Hier wird ein Überblick darüber, wie Visual Studio die lokalen Variablen für eine Methode aus der Auswertung eines Ausdrucks \(EE\) erhält:  
  
1.  Visual Studio ruft das Debuggen Modul \(DE\) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) zum Abrufen einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) \-Objekt, das alle Eigenschaften des Stapelrahmens, einschließlich der lokalen Variablen darstellt.  
  
2.  `IDebugStackFrame2::GetDebugProperty` Aufrufe [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) um ein Objekt abzurufen, die die Methode beschreibt, in dem der Haltepunkt aufgetreten ist. Die DE stellt einen Symbol\-Anbieter \([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)\), eine Adresse \([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)\), und \([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)\).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` Ruft [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) mit dem angegebenen `IDebugAddress` abzurufenden Objekts eine [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) die Methode mit der angegebenen Adresse darstellt.  
  
4.  Die `IDebugContainerField` Schnittstelle abgefragt wird, für die [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) Schnittstelle. Es ist dieser Schnittstelle, die die Methode "lokal" gewährt.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` instanziiert eine Klasse \(namens `CFieldProperty` im Beispiel\), implementiert die `IDebugProperty2` Schnittstelle, um die Methode "lokal" darzustellen. Die `IDebugMethodField` in diesem Objekt platziert `CFieldProperty` \-Objekts zusammen mit den `IDebugSymbolProvider`, `IDebugAddress` und `IDebugBinder` Objekte.  
  
6.  Wenn die `CFieldProperty` \-Objekt initialisiert wird, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) aufgerufen wird die `IDebugMethodField` \-Objekts zum Abrufen einer [FIELD\_INFO](../../extensibility/debugger/reference/field-info.md) Struktur, die alle anzeigbaren Informationen über die Methode selbst enthält.  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` Gibt die `CFieldProperty` \-Objekt als ein `IDebugProperty2` Objekt.  
  
8.  Visual Studio Aufrufe [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) für das zurückgegebene `IDebugProperty2` Objekt mit dem Filter `guidFilterLocalsPlusArgs`. Dies gibt eine [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) \-Objekt, das die Methode "lokal" enthält. Diese Enumeration wird durch Aufrufen von ausgefüllt [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) und [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio Aufrufe [Weiter](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) zum Abrufen einer [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) Struktur für jede lokale. Diese Struktur enthält einen Zeiger auf eine `IDebugProperty2` Schnittstelle für eine lokale.  
  
10. Visual Studio Aufrufe [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) für jede lokale um des lokalen Namen, Wert und Typ zu erhalten. Dies sind die Informationen, die in angezeigt wird der **Lokal** Fenster.  
  
## In diesem Abschnitt  
 [Implementieren von GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Wird eine Implementierung von [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Auflisten von lokalen Variablen](../../extensibility/debugger/enumerating-locals.md)  
 Beschreibt, wie das Debugging\-Modul \(DE\) Auflisten von lokalen Variablen oder Argumente aufruft.  
  
 [Lokale Eigenschaften abrufen](../../extensibility/debugger/getting-local-properties.md)  
 Beschreibt, wie die DE Name, Typ und Wert, der eine oder mehrere lokale Variablen erhalten aufruft.  
  
 [Lokale Werte abrufen](../../extensibility/debugger/getting-local-values.md)  
 Erläutert, Abrufen des Werts der lokalen, der Dienste eines Binder\-Objekts, das vom Evaluierungskontext erforderlich ist.  
  
 [Auswertung der lokalen Variablen](../../extensibility/debugger/evaluating-locals.md)  
 Erläutert, wie lokal ausgewertet werden.  
  
## Verwandte Abschnitte  
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md)  
 Stellt die Argumente übergeben werden, wenn die DE der Auswertung eines Ausdrucks \(EE\) aufruft.  
  
 [MyCEE Sample](http://msdn.microsoft.com/de-de/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Zeigt eine Implementierungsansatz zum Erstellen einer Auswertung eines Ausdrucks für die Sprache MyC.  
  
## Siehe auch  
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)