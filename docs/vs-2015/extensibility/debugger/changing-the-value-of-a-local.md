---
title: Ändern des Werts eines lokalen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 516725510c5f5bc7baa8bd96d3f7fb969b6589e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840862"
---
# <a name="changing-the-value-of-a-local"></a>Ändern des Werts eines lokalen Elements
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn ein neuer Wert im Feld Wert **des Fensters Lokal** eingegeben wird, übergibt das Debugpaket die als typisierte Zeichenfolge an die-Ausdrucks Auswertung (EE). Der EE wertet diese Zeichenfolge aus, die entweder einen einfachen Wert oder einen Ausdruck enthalten kann, und speichert den resultierenden Wert in der zugeordneten lokalen.  
  
 Dies ist eine Übersicht über den Prozess der Änderung des Werts eines lokalen:  
  
1. Nachdem der Benutzer den neuen Wert eingegeben hat, ruft Visual Studio [setvalueasstring](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) für das [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Objekt auf, das mit dem lokalen verknüpft ist.  
  
2. `IDebugProperty2::SetValueAsString` führt folgende Ausgaben aus:  
  
   1. Wertet die Zeichenfolge aus, um einen Wert zu erhalten.  
  
   2. Bindet das zugeordnete [idebugfield](../../extensibility/debugger/reference/idebugfield.md) -Objekt an das Abrufen eines [idebugobject](../../extensibility/debugger/reference/idebugobject.md) -Objekts.  
  
   3. Konvertiert den Wert in eine Reihe von Bytes.  
  
   4. Ruft [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) auf, um die Bytes des Werts in den Speicher zu versetzen, damit das Programm, das gedeppt wird, darauf zugreifen kann  
  
3. Visual Studio aktualisiert die **lokale** Anzeige (Weitere Informationen finden Sie unter [Anzeigen von lokalen](../../extensibility/debugger/displaying-locals.md) Informationen).  
  
   Diese Prozedur wird auch verwendet, um den Wert einer Variablen im Fenster über **Wachen** zu ändern, es sei denn, es handelt sich um das `IDebugProperty2` Objekt, das dem Wert des lokalen zugeordnet ist, das anstelle des Objekts verwendet wird, `IDebugProperty2` das dem lokalen selbst zugeordnet ist.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Beispielimplementierung der Änderungen von Werten](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Verwendet das mycee-Beispiel, um den Prozess der Änderung von Werten schrittweise zu durchlaufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)
