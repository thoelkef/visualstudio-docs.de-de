---
title: 'CA1009: Ereignishandler korrekt deklarieren | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d207bff88129cb9cc6769cc47ae6e70cbe74d1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Ereignishandler korrekt deklarieren
|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Delegat, der eine öffentliche oder geschützte Ereignisbehandlung besitzt nicht die richtige Signatur, den Rückgabetyp oder Parameternamen.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ereignishandlermethoden nehmen zwei Parameter an. Die erste ist vom Typ <xref:System.Object?displayProperty=fullName> und ist mit dem Namen "Sender". Dies ist das Objekt, durch das das Ereignis ausgelöst wurde. Der zweite Parameter ist vom Typ <xref:System.EventArgs?displayProperty=fullName> und ist mit dem Namen "e". Dies sind die Daten, die dem Ereignis zugeordnet sind. Z. B. wenn das Ereignis ausgelöst wird, wenn eine Datei geöffnet ist, das die Ereignisdaten enthält i. d. r. der Name der Datei.  
  
 Ereignishandlermethoden sollten keinen Wert zurück. In der Programmiersprache c# wird dies durch den Rückgabetyp angegeben `void`. Ein Ereignishandler kann mehrere Methoden in mehreren Objekten aufrufen. Wenn die Methoden zugelassen wird, einen Wert zurückzugeben, kommt es mehrere Rückgabewerte für jedes Ereignis, und nur der Wert von der letzten aufgerufenen Methode zur Verfügung.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Signatur, den Rückgabetyp oder die Parameternamen des Delegaten. Weitere Informationen finden Sie im folgende Beispiel.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt ein Delegat, der für die Behandlung von Ereignissen geeignet ist. Die Methoden, die von diesem Ereignishandler aufgerufen werden können einhalten, die Signatur, die in den Entwurfsrichtlinien angegeben wird. `AlarmEventHandler` ist der Typname des Delegaten an. `AlarmEventArgs` leitet sich von der Basisklasse für Ereignisdaten, <xref:System.EventArgs>, und enthält alarm Ereignisdaten.  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2109: Sichtbare Ereignishandler überprüfen](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [Behandeln und Auslösen von Ereignissen](/dotnet/standard/events/index)  