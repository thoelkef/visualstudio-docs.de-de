---
title: 'CA1001: Typen, die löschbare Felder besitzen sollten gelöscht werden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bf86ab422851e27eafbb165968d4005cba7ecf5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515171"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend – Wenn der Typ nicht außerhalb der Assembly sichtbar ist.<br /><br /> Wichtige – Wenn der Typ außerhalb der Assembly sichtbar ist.|  
  
## <a name="cause"></a>Ursache  
 Eine Klasse deklariert und implementiert ein Instanzenfeld, das eine <xref:System.IDisposable?displayProperty=fullName> Typ und die Klasse implementiert keine <xref:System.IDisposable>.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Eine Klasse implementiert die <xref:System.IDisposable> Schnittstelle, um nicht verwaltete Ressourcen freigegeben, die dieser besitzt. Ein Instanzenfeld, das eine <xref:System.IDisposable> Typ gibt an, dass das Feld eine nicht verwaltete Ressource besitzt. Eine Klasse, die deklariert eine <xref:System.IDisposable> Feld indirekt eine nicht verwaltete Ressource besitzt, und sollte implementieren die <xref:System.IDisposable> Schnittstelle. Wenn die Klasse nicht direkt über nicht verwalteten Ressourcen besitzt, sollten sie keinen Finalizer implementieren.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren <xref:System.IDisposable> und von der <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Methodenaufruf der <xref:System.IDisposable.Dispose%2A> -Methode des Felds.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Klasse, die gegen die Regel verstößt und eine Klasse, die durch die Implementierung der Regel entspricht <xref:System.IDisposable>. Die Klasse implementiert keinen Finalizer, da die Klasse nicht direkt über nicht verwalteten Ressourcen besitzt.  
  
 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: Typen, die systemeigene Ressourcen besitzen, müssen gelöscht werden können](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

