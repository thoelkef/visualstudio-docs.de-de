---
title: 'CA1003: Generische Ereignishandlerinstanzen verwenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 26630aa008e944f0af3fdcc66a16dc4c08bd4e8b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887331"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Generische Ereignishandlerinstanzen verwenden

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ enthält einen Delegaten, die "void" zurückgibt, deren Signatur enthält zwei Parameter (der erste ist ein Objekt und das zweite ein Typ, der EventArgs zugewiesen werden) und die Ziele der enthaltenden Assembly [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Regelbeschreibung
 Vor dem [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], um benutzerdefinierte Informationen an den Ereignishandler übergeben musste, dass ein neuer Delegat deklariert werden, die eine Klasse, die von abgeleitet wurde angegeben, die <xref:System.EventArgs?displayProperty=fullName> Klasse. Dies ist nicht mehr in "true" [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], eingeführt, die <xref:System.EventHandler%601?displayProperty=fullName> delegieren. Dieser generische Delegat kann jede Klasse, die abgeleitet wird <xref:System.EventArgs> , zusammen mit der Ereignishandler verwendet werden soll.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Delegaten, und Ersetzen Sie die Verwendung durch die <xref:System.EventHandler%601?displayProperty=fullName> delegieren. Wenn der Delegat automatisch von der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] -Compiler, ändern Sie die Syntax der Deklaration des Ereignisses mit der <xref:System.EventHandler%601?displayProperty=fullName> delegieren.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein Delegat, der gegen die Regel verstößt. In der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] beispielsweise Kommentare beschrieben, wie Sie das Beispiel, um die Regel erfüllen zu ändern. Für das C#-Beispiel folgt ein Beispiel, das den geänderten Code zeigt.

 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel entfernt der Delegatdeklaration überein, aus dem vorherigen Beispiel, in der Regel entspricht, und ersetzt die Verwendung in der `ClassThatRaisesEvent` und `ClassThatHandlesEvent` Methoden mithilfe der <xref:System.EventHandler%601?displayProperty=fullName> delegieren.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member in generischen Typen nicht deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: NACH MÖGLICHKEIT Verwenden Sie Generika](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch

- [Generika](/dotnet/csharp/programming-guide/generics/index)