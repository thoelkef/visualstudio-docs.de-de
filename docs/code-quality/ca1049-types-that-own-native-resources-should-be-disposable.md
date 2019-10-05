---
title: 'CA1049: Typen, die native Ressourcen besitzen, müssen gelöscht werden können.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: ef7b72eade7ea8e4486d5c317c06026bb4d0b95f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235742"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typen, die native Ressourcen besitzen, müssen gelöscht werden können.

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ verweist auf <xref:System.IntPtr?displayProperty=fullName> ein Feld, <xref:System.UIntPtr?displayProperty=fullName> ein Feld oder ein <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> Feld, implementiert <xref:System.IDisposable?displayProperty=fullName>jedoch nicht.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel setzt voraus <xref:System.IntPtr>, <xref:System.UIntPtr>dass die <xref:System.Runtime.InteropServices.HandleRef> Felder, und Zeiger auf nicht verwaltete Ressourcen speichern. Typen, die nicht verwaltete Ressourcen zuordnen, <xref:System.IDisposable> sollten implementieren, damit Aufrufer diese Ressourcenbedarfs gesteuert freigeben und die Lebensdauer der Objekte verkürzen können, die die Ressourcen enthalten.

Das empfohlene Entwurfsmuster zum Bereinigen nicht verwalteter Ressourcen besteht darin, ein implizites und explizites Mittel bereitzustellen, um <xref:System.Object.Finalize%2A?displayProperty=fullName> diese Ressourcen mithilfe <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> der-Methode bzw. der-Methode freizugeben. Der Garbage Collector Ruft die <xref:System.Object.Finalize%2A> -Methode eines-Objekts zu einer unbestimmten Zeit auf, nachdem festgestellt wurde, dass das Objekt nicht mehr erreichbar ist. Nachdem <xref:System.Object.Finalize%2A> aufgerufen wurde, ist ein zusätzlicher Garbage Collection erforderlich, um das Objekt freizugeben. Die <xref:System.IDisposable.Dispose%2A> -Methode ermöglicht es dem Aufrufer, Ressourcen bei Bedarf explizit freizugeben, bevor die Ressourcen freigegeben werden, wenn Sie an die Garbage Collector weitergegeben werden. Nachdem die nicht verwalteten Ressourcen bereinigt wurden, <xref:System.IDisposable.Dispose%2A> sollte die- <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> Methode aufrufen, um die Garbage Collector zu informieren, <xref:System.Object.Finalize%2A> dass nicht mehr aufgerufen werden muss. Dadurch entfällt die Notwendigkeit zusätzlicher Garbage Collection und verkürzt das die Lebensdauer des Objekts.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, <xref:System.IDisposable>implementieren Sie.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Typ nicht auf eine nicht verwaltete Ressource verweist. Andernfalls sollten Sie keine Warnung aus dieser Regel unterdrücken, weil die Implementierung <xref:System.IDisposable> von nicht verwalteten Ressourcen zu nicht verfügbaren oder nicht genutzten Ressourcen führen kann.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der <xref:System.IDisposable> implementiert, um eine nicht verwaltete Ressource zu bereinigen.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2115: Ruft GC auf. KeepAlive bei der Verwendung nativer Ressourcen](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Ruft GC auf. Ordnungsgemäße SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Siehe auch

- [Bereinigen von nicht verwalteten Ressourcen](/dotnet/standard/garbage-collection/unmanaged)
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)