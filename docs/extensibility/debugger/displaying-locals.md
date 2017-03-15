---
title: "Anzeigen von lokalen Variablen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen die Auswertung von Ausdrücken [Debuggen SDK]"
  - "Auswertung von Ausdrücken, lokale Variablen anzeigen"
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Anzeigen von lokalen Variablen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Immer die Ausführung erfolgt im Kontext einer Methode, auch bekannt als der enthaltenden Methode oder die aktuelle Methode. Wenn die Ausführung angehalten wird, ruft Visual Studio den Debugging\-Modul \(DE\) zum Abrufen einer Liste von lokalen Variablen und Argumente, die zusammen die lokalen Variablen der Methode aufgerufen. Visual Studio zeigt diese lokalen Variablen und deren Werte in den **Lokal** Fenster.  
  
 Um lokale Variablen anzuzeigen, die DE Ruft die [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) Methode der EE und ihm einen Evaluierungskontext, der, ein Symbol\-Anbieter \(SP\), die aktuelle Ausführung Adresse und ein Binder\-Objekt. Weitere Informationen finden Sie unter [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md). Wenn der Aufruf erfolgreich ist, die `IDebugExpressionEvaluator::GetMethodProperty` \-Methode gibt ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) \-Objekt, das die Methode darstellt, die die aktuelle Ausführung Adresse enthält.  
  
 DE Aufrufe [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) zum Abrufen einer [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) \-Objekt, das gefiltert, dass nur lokale Variablen zurückgegeben und aufgelistet, um eine Liste erzeugt [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) Strukturen. Jede Struktur enthält die Namen, Typ und Wert eines lokalen. Der Typ und Wert werden als geeignet für die Anzeige formatierte Zeichenfolgen gespeichert. Der Name, Typ und Wert sind in der Regel zusammen in einer einzigen Codezeile angezeigt der **Lokal** Fenster.  
  
> [!NOTE]
>  Die **Schnellüberwachung** und **Überwachen** Windows auch Variablen mit dem gleichen Format der Namen, Wert und Typ angezeigt. Diese Werte werden jedoch durch Aufrufen abgerufen [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) anstelle von `IDebugProperty2::EnumChildren`.  
  
## In diesem Abschnitt  
 [Beispielimplementierung von lokalen Variablen](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Werden Sie schrittweise durch den Prozess der Implementierung von lokal Beispiele verwendet.  
  
## Verwandte Abschnitte  
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md)  
 Erklärt, wenn das Debugging\-Modul \(DE\) der Auswertung eines Ausdrucks \(EE\) aufruft, er drei Argumente übergibt.  
  
## Siehe auch  
 [Schreiben Sie eine CLR\-Ausdrucksauswerter](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)