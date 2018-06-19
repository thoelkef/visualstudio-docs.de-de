---
title: Ändern des Werts eines lokalen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 422d1702f319db6da21892bcaa1bd50adad7909d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109584"
---
# <a name="changing-the-value-of-a-local"></a>Ändern des Werts von einer lokalen
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn ein neuer Wert in das Wertfeld des typisiert ist die **"lokal"** Fenster übergibt das debugpaket die Zeichenfolge an, wie der ausdrucksauswertung (EE) eingegeben haben. Die EE wertet dieser Zeichenfolge übereinstimmt, kann ein einfacher Wert oder einen Ausdruck enthalten, und speichert den resultierenden Wert in der zugeordneten lokalen.  
  
 Dies ist eine Übersicht über den Prozess der Änderung des Werts eines lokalen:  
  
1.  Nachdem der Benutzer den neuen Wert eingegeben hat, ruft Visual Studio [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) auf die [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das mit der lokalen zugeordnet.  
  
2.  `IDebugProperty2::SetValueAsString` führt folgende Ausgaben aus:  
  
    1.  Wertet die Zeichenfolge, um einen Wert zu erzeugen.  
  
    2.  Bindet das zugeordnete [IDebugField](../../extensibility/debugger/reference/idebugfield.md) Objekt zum Abrufen einer [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) Objekt.  
  
    3.  Konvertiert den Wert in eine Reihe von Bytes.  
  
    4.  Aufrufe [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) Bytes der Wert in den Arbeitsspeicher eingefügt wird, damit zu debuggenden Programms darauf zugreifen kann.  
  
3.  Visual Studio aktualisiert die **"lokal"** angezeigt (finden Sie unter [anzeigen "lokal"](../../extensibility/debugger/displaying-locals.md) Einzelheiten).  
  
 Dieses Verfahren dient außerdem zum Ändern des Werts einer Variablen in der **Überwachen** Fenster, es sei denn, es ist die `IDebugProperty2` Objekt zugewiesen ist, mit dem Wert der lokalen, die anstelle von verwendet wird die `IDebugProperty2` mit der lokalen selbst.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Beispielimplementierung der Änderungen von Werten](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Die MyCEE-Beispiel verwendet schrittweise durch den Prozess zum Ändern von Werten.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)