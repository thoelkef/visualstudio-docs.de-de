---
title: 'CA2136: Member sollten keine in Konflikt stehenden transparenzanmerkungen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6b77dfdbb97d54e5ad1ac31d3f5e29a03cd9b54
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Member dürfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen
|||  
|-|-|  
|TypeName|TransparencyAnnotationsShouldNotConflict|  
|CheckId|CA2136|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Diese Regel wird ausgelöst, wenn Sie ein Typmember mit gekennzeichnet ist eine <xref:System.Security> Security-Attribut, das eine andere als das Sicherheitsattribut eines Containers des Members Transparenz.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Transparenzattribute werden von größeren Codeelementen bis hin zu kleineren Elementen übernommen. Die Transparenzattribute von Codeelementen mit größerem Umfang haben Vorrang vor Transparenzattributen von Codeelementen, die im ersten Element enthalten sind. Z. B. eine Klasse, die mit der <xref:System.Security.SecurityCriticalAttribute> -Attribut darf nicht enthalten eine Methode, die mit der <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um diese Verstoß zu beheben, entfernen Sie das Sicherheitsattribut aus dem Codeelement, das untere Bereich aufweist, oder ändern Sie das Attribut aus, um das enthaltende Codeelement identisch sein.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine Methode mit markiert die <xref:System.Security.SecuritySafeCriticalAttribute> -Attribut, und es ist ein Member einer Klasse, die mit der <xref:System.Security.SecurityCriticalAttribute> Attribut. Das sichere Attribut sollte entfernt werden.  
  
 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]