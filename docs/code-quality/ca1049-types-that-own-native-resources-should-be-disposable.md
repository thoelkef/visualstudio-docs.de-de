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
ms.openlocfilehash: 03b8d222fc2349022ef324c9905279677fc86849
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306119"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typen, die native Ressourcen besitzen, müssen gelöscht werden können.

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ verweist auf ein <xref:System.IntPtr?displayProperty=fullName>-Feld, ein <xref:System.UIntPtr?displayProperty=fullName>-Feld oder ein <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>-Feld, implementiert jedoch <xref:System.IDisposable?displayProperty=fullName> nicht.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel setzt voraus, dass die Felder "<xref:System.IntPtr>", "<xref:System.UIntPtr>" und "<xref:System.Runtime.InteropServices.HandleRef>" Zeiger auf nicht verwaltete Ressourcen speichern. Typen, die nicht verwaltete Ressourcen zuordnen, sollten <xref:System.IDisposable> implementieren, damit Aufrufer diese Ressourcenbedarfs gesteuert freigeben und die Lebensdauer der Objekte verkürzen können, die die Ressourcen enthalten.

Das empfohlene Entwurfsmuster zum Bereinigen nicht verwalteter Ressourcen besteht darin, ein implizites und explizites Mittel bereitzustellen, um diese Ressourcen mit der <xref:System.Object.Finalize%2A?displayProperty=fullName>-Methode bzw. der Methode <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> freizugeben. Der Garbage Collector Ruft die <xref:System.Object.Finalize%2A>-Methode eines Objekts zu einer unbestimmten Zeit auf, nachdem festgestellt wurde, dass das Objekt nicht mehr erreichbar ist. Nachdem <xref:System.Object.Finalize%2A> aufgerufen wurde, ist ein zusätzlicher Garbage Collection erforderlich, um das Objekt freizugeben. Die <xref:System.IDisposable.Dispose%2A>-Methode ermöglicht dem Aufrufer das explizite Freigeben von Ressourcen bei Bedarf, bevor die Ressourcen freigegeben werden, wenn Sie für die Garbage Collector übrig bleiben. Nachdem die nicht verwalteten Ressourcen bereinigt wurden, sollte <xref:System.IDisposable.Dispose%2A> die <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>-Methode aufrufen, um die Garbage Collector zu informieren, dass <xref:System.Object.Finalize%2A> nicht mehr aufgerufen werden muss. Dadurch entfällt die Notwendigkeit zusätzlicher Garbage Collection und verkürzt die Lebensdauer des Objekts.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Typ nicht auf eine nicht verwaltete Ressource verweist. Andernfalls sollten Sie keine Warnung aus dieser Regel unterdrücken, weil die Implementierung von <xref:System.IDisposable> dazu führen kann, dass nicht verwaltete Ressourcen nicht mehr verfügbar oder unterausgelastet werden.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der <xref:System.IDisposable> implementiert, um eine nicht verwaltete Ressource zu bereinigen.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2115: Ruft GC auf. KeepAlive bei Verwendung nativer Ressourcen @ no__t-0

[CA1816: Ruft GC auf. SuppressFinalize ordnungsgemäß @ no__t-0

[CA2216: Verwerfbare Typen sollten den Finalizer @ no__t-0 deklarieren.

[CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Siehe auch

- [Bereinigen von nicht verwalteten Ressourcen](/dotnet/standard/garbage-collection/unmanaged)
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)