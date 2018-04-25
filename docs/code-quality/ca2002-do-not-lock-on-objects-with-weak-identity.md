---
title: 'CA2002: Auf Objekten mit schwacher Identität nicht sperren'
ms.date: 01/31/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 868ed0e1b4b5581473f7c7bde98f6f40e29f0664
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: Auf Objekten mit schwacher Identität nicht sperren

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Thread versucht, eine Sperre für ein Objekt zu erhalten, die eine schwache Identität verfügt.

## <a name="rule-description"></a>Regelbeschreibung

Ein Objekt hat eine schwache Identität, wenn ein Zugriff darauf über Grenzen von Anwendungsdomänen hinweg möglich ist. Ein Thread, der eine Sperre für ein Objekt zu erhalten versucht, das über eine schwache Identität verfügt, kann durch einen zweiten Thread in einer anderen Anwendungsdomäne blockiert werden, der eine Sperre für das gleiche Objekt besitzt.

Die folgenden Typen haben eine schwache Identität und werden von der Regel gekennzeichnet:

- <xref:System.String>

- Arrays von Werttypen, einschließlich [Ganzzahltypen](/dotnet/csharp/language-reference/keywords/integral-types-table), [Gleitkommatypen](/dotnet/csharp/language-reference/keywords/floating-point-types-table), und <xref:System.Boolean>.

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie ein Objekt von einem Typ, der nicht in der Liste im Abschnitt "Beschreibung" ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln

[CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einige Objektsperren, die die Regel verletzen.

[!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
[!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]

## <a name="see-also"></a>Siehe auch

<xref:System.Threading.Monitor>
<xref:System.AppDomain>
[lock-Anweisung (c#)](/dotnet/csharp/language-reference/keywords/lock-statement)
[SyncLock-Anweisung (Visual Basic)](/dotnet/visual-basic/language-reference/statements/synclock-statement)