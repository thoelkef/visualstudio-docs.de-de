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
ms.openlocfilehash: aaaf95346c51e2cb5cadb01a39e482bb508bc764
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668908"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typen, die systemeigene Ressourcen besitzen, müssen gelöscht werden können
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ verweist auf ein <xref:System.IntPtr?displayProperty=fullName>-Feld, ein <xref:System.UIntPtr?displayProperty=fullName>-Feld oder ein <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>-Feld, implementiert jedoch <xref:System.IDisposable?displayProperty=fullName> nicht.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel setzt voraus, dass die Felder "<xref:System.IntPtr>", "<xref:System.UIntPtr>" und "<xref:System.Runtime.InteropServices.HandleRef>" Zeiger auf nicht verwaltete Ressourcen speichern. Typen, die nicht verwaltete Ressourcen zuordnen, sollten <xref:System.IDisposable> implementieren, damit Aufrufer diese Ressourcenbedarfs gesteuert freigeben und die Lebensdauer der Objekte verkürzen können, die die Ressourcen enthalten.

 Das empfohlene Entwurfsmuster zum Bereinigen nicht verwalteter Ressourcen besteht darin, ein implizites und explizites Mittel bereitzustellen, um diese Ressourcen mit der <xref:System.Object.Finalize%2A?displayProperty=fullName>-Methode bzw. der <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>-Methode freizugeben. Der Garbage Collector Ruft die <xref:System.Object.Finalize%2A>-Methode eines Objekts zu einer unbestimmten Zeit auf, nachdem festgestellt wurde, dass das Objekt nicht mehr erreichbar ist. Nachdem <xref:System.Object.Finalize%2A> aufgerufen wurde, ist ein zusätzlicher Garbage Collection erforderlich, um das Objekt freizugeben. Die <xref:System.IDisposable.Dispose%2A>-Methode ermöglicht dem Aufrufer das explizite Freigeben von Ressourcen bei Bedarf, bevor die Ressourcen freigegeben werden, wenn Sie auf die Garbage Collector zurückgegeben werden. Nachdem die nicht verwalteten Ressourcen bereinigt wurden, sollten <xref:System.IDisposable.Dispose%2A> die <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>-Methode aufrufen, um die Garbage Collector zu informieren, dass <xref:System.Object.Finalize%2A> nicht mehr aufgerufen werden muss. Dadurch entfällt die Notwendigkeit zusätzlicher Garbage Collection und verkürzt die Lebensdauer des Objekts.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Typ nicht auf eine nicht verwaltete Ressource verweist. Andernfalls sollten Sie keine Warnung aus dieser Regel unterdrücken, weil die Implementierung von <xref:System.IDisposable> dazu führen kann, dass nicht verwaltete Ressourcen nicht mehr verfügbar oder unterausgelastet werden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der <xref:System.IDisposable> implementiert, um eine nicht verwaltete Ressource zu bereinigen.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2115: GC.KeepAlive beim Verwenden systemeigener Ressourcen aufrufen](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: GC.SuppressFinalize korrekt aufrufen](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Siehe auch
  [Dispose-Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
