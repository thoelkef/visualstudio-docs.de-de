---
title: "&#196;ndern des Werts von einer lokalen | Microsoft Docs"
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
  - "Auswertung von Ausdrücken, die Werte programmgesteuert ändern."
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# &#196;ndern des Werts von einer lokalen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn ein neuer Wert eingegeben wird, in das Wertefeld, der die **Lokal** Fenster, das debugpaket übergibt die Zeichenfolge wie für die ausdrucksauswertung \(EE\) eingegeben. Die EE wertet diese Zeichenfolge, die einen einfachen Wert oder einen Ausdruck enthalten kann, und speichert den resultierenden Wert in der zugehörigen lokalen.  
  
 Dies ist eine Übersicht über das Ändern des Werts von einer lokalen:  
  
1.  Nachdem der neue Wert eingegeben wurde, ruft Visual Studio [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) auf den [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) der lokalen zugeordnete Objekt.  
  
2.  `IDebugProperty2::SetValueAsString` die folgenden Aufgaben ausgeführt:  
  
    1.  Wertet die Zeichenfolge aus, um einen Wert zu erzeugen.  
  
    2.  Bindet das zugeordnete [IDebugField](../../extensibility/debugger/reference/idebugfield.md) \-Objekts zum Abrufen einer [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) Objekt.  
  
    3.  Konvertiert den Wert in eine Reihe von Bytes.  
  
    4.  Aufrufe [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) Bytes der Wert in den Speicher ablegen, damit gedebuggte Programm darauf zugreifen kann.  
  
3.  Visual Studio aktualisiert das **Lokal** anzeigen \(finden Sie unter [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md) Details\).  
  
 Dieses Verfahren wird auch verwendet, um den Wert einer Variablen im Ändern der **Überwachen** Fenster, es sei denn, es ist die `IDebugProperty2` Objekt zugeordnet, mit dem Wert der lokalen, die anstelle von verwendet wird die `IDebugProperty2` \-Objekt der lokalen selbst zugeordnet.  
  
## In diesem Abschnitt  
 [Beispielimplementierung der Werte ändern](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 MyCEE Beispiel verwendet zum Ändern der Werte schrittweise.  
  
## Siehe auch  
 [Schreiben Sie eine CLR\-Ausdrucksauswerter](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)