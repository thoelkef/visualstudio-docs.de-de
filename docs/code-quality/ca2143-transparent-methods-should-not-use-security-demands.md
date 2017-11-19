---
title: 'CA2143: Transparente Methoden sollten nicht verwenden, sicherheitsforderungen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 22adac09d7890f9d15e0bf50f46235f4b48d73dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Transparente Methoden dürfen keine Sicherheitsanforderungen verwenden
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|CheckId|CA2143|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Einer transparenten Typ oder Methode RuntimeCompatibility deklarativ mit einer <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` bei Bedarf oder Methodenaufrufe der <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> Methode.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Sicherheitstransparenter Code sollte mithilfe von vollständigen Anforderungen Sicherheitsentscheidungen fällen, und sicherheitskritischer Code sollte für die vollständige Anforderung nicht auf transparentem Code beruhen. Stattdessen sollte jeglicher Code, der von sicherheitsüberprüfungen, z. B. sicherheitsforderungen, führt sicherheitsgeschützt sein.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 In der Regel um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode mit dem <xref:System.Security.SecuritySafeCriticalAttribute> Attribut. Sie können auch den Bedarf entfernen.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Die Regel Dateien auf den folgenden Code, da eine transparente Methode einen deklarative Sicherheit bei Bedarf wird.  
  
 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)