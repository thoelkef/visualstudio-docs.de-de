---
title: 'CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1616e889b3892aa656692a3e5b0895d4b131b7f1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231253"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren.

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ, der <xref:System.IDisposable?displayProperty=fullName>implementiert und über Felder verfügt, die die Verwendung nicht verwalteter Ressourcen vorschlagen, implementiert keinen Finalizer, wie in <xref:System.Object.Finalize%2A?displayProperty=fullName>beschrieben.

## <a name="rule-description"></a>Regelbeschreibung

Ein Verstoß gegen diese Regel wird gemeldet, wenn der verwerfbare Typ Felder der folgenden Typen enthält:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie <xref:System.IDisposable.Dispose%2A> einen Finalizer, der die-Methode aufruft.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Typ <xref:System.IDisposable> nicht implementiert, um nicht verwaltete Ressourcen freizugeben.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln

[CA2115: Ruft GC auf. KeepAlive bei der Verwendung nativer Ressourcen](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Ruft GC auf. Ordnungsgemäße SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049: Typen, die native Ressourcen besitzen, müssen gelöscht werden können](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)