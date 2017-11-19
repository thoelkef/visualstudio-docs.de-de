---
title: 'CA1003: Generische Ereignishandlerinstanzen verwenden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf4f11f3f8fae1130c2cc99468a40ed269c77481
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Generische Ereignishandlerinstanzen verwenden
|||  
|-|-|  
|TypeName|UseGenericEventHandlerInstances|  
|CheckId|CA1003|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Typ enthält einen Delegaten, die "void" zurückgibt, dessen Signatur enthält zwei Parameter (der erste ist ein Objekt und der zweite ein Typ, der EventArgs zugewiesen werden kann) und die enthaltende Assembly Ziele [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Vor dem [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], um benutzerdefinierte Informationen an den Ereignishandler übergeben ein neuer Delegat deklariert werden, die eine Klasse, die abgeleitet wurde angegeben hatten die <xref:System.EventArgs?displayProperty=fullName> Klasse. Dies ist nicht mehr in "true" [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], welche eingeführt der <xref:System.EventHandler%601?displayProperty=fullName> delegieren. Dieser generische Delegat ermöglicht es, jede Klasse, die abgeleitet ist <xref:System.EventArgs> zusammen mit der Ereignishandler verwendet werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Delegaten und dessen Verwendung durch Ersetzen der <xref:System.EventHandler%601?displayProperty=fullName> delegieren. Wenn der Delegat automatisch von der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] -Compiler, ändern Sie die Syntax der Deklaration des Ereignisses zum Verwenden der <xref:System.EventHandler%601?displayProperty=fullName> delegieren.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt ein Delegat, der die Regel verletzt. In der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] beispielsweise Kommentare beschrieben, wie Sie die Regel erfüllen anhand des Beispiels zu ändern. Das C#-Beispiel folgt ein Beispiel mit dem geänderten Code angezeigt.  
  
 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel entfernt der Delegatdeklaration überein, aus dem vorherigen Beispiel, in der Regel entspricht, und ersetzt die Verwendung in der `ClassThatRaisesEvent` und `ClassThatHandlesEvent` Methoden mithilfe der <xref:System.EventHandler%601?displayProperty=fullName> delegieren.  
  
 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1007: Nach Möglichkeit Generika verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Generika](/dotnet/csharp/programming-guide/generics/index)