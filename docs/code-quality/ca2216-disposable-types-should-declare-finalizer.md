---
title: 'CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f53f91a6a4775fb17e273fb87c4c669f74ad45e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825996"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein Typ, der implementiert <xref:System.IDisposable?displayProperty=fullName>, und enthält Felder, die die Verwendung von nicht verwalteten Ressourcen wird empfohlen, einen Finalizer ist nicht implementiert werden, wie beschrieben <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung

Ein Verstoß gegen diese Regel wird gemeldet, wenn die verwerfbaren Typs Felder der folgenden Typen enthält:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie einen Finalizer, der Aufrufe Ihrer <xref:System.IDisposable.Dispose%2A> Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicherer, die mit dieser Regel eine Warnung zu unterdrücken, wenn der Typ nicht implementiert <xref:System.IDisposable> für die Freigabe nicht verwalteter Ressourcen.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln

[CA2115: Rufen Sie GC. KeepAlive beim Verwenden systemeigener Ressourcen](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Rufen Sie GC. SuppressFinalize ordnungsgemäß](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049: Typen, die systemeigene Ressourcen besitzen müssen gelöscht werden können.](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)