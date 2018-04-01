---
title: 'CA2142: Transparenter Code sollte nicht mit LinkDemands geschützt werden | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5d0094d8afa2dcf59efe0aace8514979d73ac921
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine transparente Methode erfordert eine <xref:System.Security.Permissions.SecurityAction> oder andere sicherheitsforderung.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel wird für transparente Methoden ausgelöst, die einen Zugriff durch LinkDemands erfordern. Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Da transparente Methoden werden neutrale Sicherheit sind bestimmt, sollten sie keine sicherheitsrelevanten vornehmen. Darüber hinaus sollten sichere kritischen Code, der Sicherheit Entscheidungen nicht auf transparentem Code auf eine solche Entscheidung zuvor vorgenommenen Vertrauensstellungen der vertrauenden Seite sein.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Linkaufruf für transparente Methode, oder markieren Sie die Methode mit <xref:System.Security.SecuritySafeCriticalAttribute> Attribut, wenn Sicherheit ausgeführt wird überprüft, wie z. B. sicherheitsforderungen.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel die Regel für die Methode wird ausgelöst, da die Methode transparent ist und mit einem LinkDemand gekennzeichnet ist <xref:System.Security.PermissionSet> , enthält eine <xref:System.Security.Permissions.SecurityAction>.  
  
 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 Unterdrücken Sie keine Warnung dieser Regel.