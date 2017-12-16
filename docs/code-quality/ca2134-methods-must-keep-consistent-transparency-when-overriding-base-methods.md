---
title: "CA2134: Methoden müssen behalten konsistenten Transparenz wahren beim Überschreiben von Basismethoden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cfeadde26330273540d8d0b4ac00911905e9760e
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Methoden müssen beim Überschreiben von Basismethoden eine konsistente Transparenz wahren
|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Diese Regel wird ausgelöst, wenn eine Methode mit markiert die <xref:System.Security.SecurityCriticalAttribute> überschreibt eine Methode, die transparent oder mit markiert ist die <xref:System.Security.SecuritySafeCriticalAttribute>. Die Regel wird auch ausgelöst, wenn eine Methode, die transparent oder mit markiert ist die <xref:System.Security.SecuritySafeCriticalAttribute> überschreibt eine Methode, die mit einem <xref:System.Security.SecurityCriticalAttribute>.  
  
 Die Regel wird angewendet, wenn eine virtuelle Methode überschrieben oder eine Schnittstelle implementiert wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Mit dieser Regel wird für Versuche zum Ändern des Sicherheitszugriff auf eine Methode, die sich weiter oben in der Vererbungskette ausgelöst. Beispielsweise ist eine virtuelle Methode in einer Basisklasse transparenten oder sicherheitsrelevanten, müssen Sie die abgeleitete Klasse es mit einer transparenten oder sicherheitsrelevanten-Methode überschrieben wird. Im Gegensatz dazu ist das virtuelle sicherheitskritisch, muss die abgeleitete Klasse es mit einer sicherheitskritischen Methode überschreiben. Die gleiche Regel gilt für die Schnittstellenmethoden implementieren.  
  
 Transparenzregeln werden erzwungen, wenn der Code JIT-kompiliert statt zur Laufzeit ist, sodass die Berechnung der Transparenz keine dynamische Typinformationen. Aus diesem Grund muss das Ergebnis der Berechnung der Transparenz ausschließlich über den statischen Typen werden JIT-kompilierte, unabhängig von der dynamische Typ nicht bestimmt werden können.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Transparenz der Methode, die eine virtuelle Methode überschrieben oder eine Schnittstelle entsprechend die Transparenz des virtuellen oder Schnittstellenmethode implementiert wird.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel. Verstöße gegen diese Regel führt zu einer Laufzeit <xref:System.TypeLoadException> für Assemblys, die Transparenz der Ebene 2 zu verwenden.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitstransparenter Code, Ebene 2](/dotnet/framework/misc/security-transparent-code-level-2)