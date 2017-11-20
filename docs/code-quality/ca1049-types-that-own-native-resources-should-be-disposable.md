---
title: "CA1049: Typen, die systemeigene Ressourcen besitzen, sollten gelöscht werden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ebcb3325cfefdfeeb95b30477c4b266a70f40eb0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typen, die systemeigene Ressourcen besitzen, müssen gelöscht werden können
|||  
|-|-|  
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Auf einen Typ verweist eine <xref:System.IntPtr?displayProperty=fullName> Feld, eine <xref:System.UIntPtr?displayProperty=fullName> Feld oder eine <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> Feld, implementiert jedoch nicht <xref:System.IDisposable?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel setzt voraus, dass <xref:System.IntPtr>, <xref:System.UIntPtr>, und <xref:System.Runtime.InteropServices.HandleRef> Felder Speichern von Zeigern auf nicht verwalteten Ressourcen. Typen, die nicht verwaltete Ressourcen zuordnen müssen implementieren <xref:System.IDisposable> damit Aufrufer diese Ressourcen bei Bedarf freigeben und zur Kürzung der Lebensdauer der Objekte, die die Ressourcen enthalten können.  
  
 Das empfohlene Entwurfsmuster zum Bereinigen von nicht verwalteten Ressourcen ist, geben Sie einen impliziten sowohl ein explizites Mittel zum Freigeben von Ressourcen mithilfe der <xref:System.Object.Finalize%2A?displayProperty=fullName> Methode und die <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> -Methode bzw.. Der Garbage Collector Ruft die <xref:System.Object.Finalize%2A> Methode eines Objekts zu einer unbestimmten Zeit, nachdem das Objekt bestimmt ist, nicht mehr erreichbar ist. Nach dem <xref:System.Object.Finalize%2A> aufgerufen wird, eine zusätzliche Garbagecollection ist erforderlich, um das Objekt frei. Die <xref:System.IDisposable.Dispose%2A> -Methode ermöglicht dem Aufrufer explizit Freigeben von Ressourcen bei Bedarf, früher als die Ressourcen freigegeben werden würden, wenn der Garbage Collector überlassen. Nachdem er die nicht verwalteten Ressourcen bereinigt <xref:System.IDisposable.Dispose%2A> sollten Aufrufen der <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> Methode, um den Garbage Collector mitzuteilen, dass <xref:System.Object.Finalize%2A> muss nicht mehr aufgerufen werden; dadurch entfällt die Notwendigkeit für die zusätzliche Garbagecollection und verkürzt die die Lebensdauer des Objekts.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren <xref:System.IDisposable>.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn der Typ nicht auf eine nicht verwaltete Ressource verweist. Andernfalls, unterdrücken Sie keine Warnung dieser Regel da implementiert <xref:System.IDisposable> kann dazu führen, dass nicht verwaltete Ressourcen nicht verfügbar oder nicht verwendet werden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, implementiert <xref:System.IDisposable> , um eine nicht verwaltete Ressource zu bereinigen.  
  
 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2115: GC.KeepAlive beim Verwenden systemeigener Ressourcen aufrufen](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816: GC.SuppressFinalize korrekt aufrufen](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Bereinigen von nicht verwalteten Ressourcen](/dotnet/standard/garbage-collection/unmanaged)   
 [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)