---
title: 'CA1003: generische Ereignishandlerinstanzen verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34318d3fb01f3f8dee50da2bc534908cecbdaf32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646301"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Generische Ereignishandlerinstanzen verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ enthält einen Delegaten, der "void" zurückgibt, dessen Signatur zwei Parameter enthält (das erste Objekt und das zweite einen Typ, der EventArgs zugewiesen werden kann), und die enthaltende Assembly ist [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Regelbeschreibung
 Bevor [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], um benutzerdefinierte Informationen an den-Ereignishandler zu übergeben, musste ein neuer Delegat deklariert werden, der eine Klasse angibt, die von der <xref:System.EventArgs?displayProperty=fullName>-Klasse abgeleitet wurde. Dies ist in [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], in der der <xref:System.EventHandler%601?displayProperty=fullName> Delegat eingeführt wurde, nicht mehr wahr. Mit diesem generischen Delegaten kann jede Klasse, die von <xref:System.EventArgs> abgeleitet ist, in Verbindung mit dem Ereignishandler verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Delegaten, und ersetzen Sie dessen Verwendung mithilfe des <xref:System.EventHandler%601?displayProperty=fullName> Delegaten. Wenn der Delegat automatisch vom [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Compiler generiert wird, ändern Sie die Syntax der Ereignis Deklaration so, dass der <xref:System.EventHandler%601?displayProperty=fullName> Delegat verwendet wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Delegaten, der gegen die Regel verstößt. Im [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Beispiel wird beschrieben, wie Sie das Beispiel ändern, um die Regel zu erfüllen. Im C# Beispiel folgt ein Beispiel, das den geänderten Code anzeigt.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Delegatdeklaration aus dem vorherigen Beispiel, die die Regel erfüllt, entfernt und deren Verwendung in den `ClassThatRaisesEvent`-und `ClassThatHandlesEvent` Methoden mithilfe des <xref:System.EventHandler%601?displayProperty=fullName> Delegaten ersetzt.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Nach Möglichkeit Generics verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
