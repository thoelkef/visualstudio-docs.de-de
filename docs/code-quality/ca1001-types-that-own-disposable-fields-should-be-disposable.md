---
title: "CA1001: Typen, die löschbare Felder besitzen sollten gelöscht werden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 30609be8b70f65cb48478c6d6d2c0f3b6d89a029
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können
|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend – Wenn der Typ nicht außerhalb der Assembly sichtbar ist.<br /><br /> Unterbrechend – Wenn der Typ außerhalb der Assembly sichtbar ist.|  
  
## <a name="cause"></a>Ursache  
 Eine Klasse deklariert und implementiert ein Instanzenfeld, das eine <xref:System.IDisposable?displayProperty=fullName> Typ und die Klasse implementiert keine <xref:System.IDisposable>.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Eine Klasse implementiert die <xref:System.IDisposable> Schnittstelle, um nicht verwaltete Ressourcen freizugeben, die er besitzt. Ein Instanzenfeld, das eine <xref:System.IDisposable> Typ gibt an, dass das Feld eine nicht verwaltete Ressource besitzt. Eine Klasse, deklariert ein <xref:System.IDisposable> Feld indirekt besitzt eine nicht verwaltete Ressource und sollte implementieren die <xref:System.IDisposable> Schnittstelle. Wenn die Klasse keine nicht verwalteten Ressourcen direkt besitzt, sollten sie einen Finalizer nicht implementieren.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren <xref:System.IDisposable> und aus der <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> -Methodenaufruf der <xref:System.IDisposable.Dispose%2A> -Methode des Felds.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Klasse, die die Regel verletzt und eine Klasse, die durch die Implementierung der Regel entspricht <xref:System.IDisposable>. Die Klasse implementieren die Finalizer nicht, da es sich bei der Klasse direkt keine nicht verwalteten Ressourcen besitzt.  
  
 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: Typen, die systemeigene Ressourcen besitzen, müssen gelöscht werden können](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)