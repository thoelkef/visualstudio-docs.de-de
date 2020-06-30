---
title: 'CA1049: Typen, die native Ressourcen besitzen, müssen gelöscht werden können | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49c56b98e3be01675c2c21cd11c2961dd75f4877
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546808"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typen, die native Ressourcen besitzen, müssen gelöscht werden können.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ verweist auf ein <xref:System.IntPtr?displayProperty=fullName> Feld, ein <xref:System.UIntPtr?displayProperty=fullName> Feld oder ein <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> Feld, implementiert jedoch nicht <xref:System.IDisposable?displayProperty=fullName> .

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel setzt voraus, dass die <xref:System.IntPtr> <xref:System.UIntPtr> Felder, und <xref:System.Runtime.InteropServices.HandleRef> Zeiger auf nicht verwaltete Ressourcen speichern. Typen, die nicht verwaltete Ressourcen zuordnen, sollten implementieren, damit Aufrufer <xref:System.IDisposable> diese Ressourcenbedarfs gesteuert freigeben und die Lebensdauer der Objekte verkürzen können, die die Ressourcen enthalten.

 Das empfohlene Entwurfsmuster zum Bereinigen nicht verwalteter Ressourcen besteht darin, ein implizites und explizites Mittel bereitzustellen, um diese Ressourcen mithilfe der <xref:System.Object.Finalize%2A?displayProperty=fullName> -Methode bzw. der-Methode freizugeben <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> . Der Garbage Collector Ruft die- <xref:System.Object.Finalize%2A> Methode eines-Objekts zu einer unbestimmten Zeit auf, nachdem festgestellt wurde, dass das Objekt nicht mehr erreichbar ist. Nachdem <xref:System.Object.Finalize%2A> aufgerufen wurde, ist ein zusätzlicher Garbage Collection erforderlich, um das Objekt freizugeben. Die- <xref:System.IDisposable.Dispose%2A> Methode ermöglicht es dem Aufrufer, Ressourcen bei Bedarf explizit freizugeben, bevor die Ressourcen freigegeben werden, wenn Sie an die Garbage Collector weitergegeben werden. Nach dem Bereinigen der nicht verwalteten Ressourcen sollte die- <xref:System.IDisposable.Dispose%2A> Methode aufrufen, <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> um die Garbage Collector zu informieren, dass <xref:System.Object.Finalize%2A> nicht mehr aufgerufen werden muss. Dadurch entfällt die Notwendigkeit zusätzlicher Garbage Collection und verkürzt die Lebensdauer des Objekts.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie <xref:System.IDisposable> .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Typ nicht auf eine nicht verwaltete Ressource verweist. Andernfalls sollten Sie keine Warnung aus dieser Regel unterdrücken, weil die Implementierung von nicht <xref:System.IDisposable> verwalteten Ressourcen zu nicht verfügbaren oder nicht genutzten Ressourcen führen kann.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der implementiert, <xref:System.IDisposable> um eine nicht verwaltete Ressource zu bereinigen.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2115: GC.KeepAlive beim Verwenden nativer Ressourcen aufrufen.](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: GC.SuppressFinalize korrekt aufrufen.](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren.](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können.](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Weitere Informationen
  [Dispose-Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
