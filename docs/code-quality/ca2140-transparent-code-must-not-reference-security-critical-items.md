---
title: 'CA2140: Transparenter Code darf nicht sicherheitskritische Elemente verweisen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0970bd3a05975707cbbac3f79dbece234adb16ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine transparente Methode:  
  
-   verarbeitet einen Sicherheit sicherheitsrelevanten Ausnahmetyp  
  
-   weist einen Parameter, der als einen sicherheitskritischen Typ gekennzeichnet ist.  
  
-   weist einen generischen Parameter mit einem kritischen sicherheitseinschränkungen  
  
-   verfügt über eine lokale Variable vom einen sicherheitskritischen Typ  
  
-   verweist auf einen Typ, der als sicherheitskritisch markiert ist  
  
-   Ruft eine Methode, die als sicherheitskritisch markiert ist  
  
-   verweist auf ein Feld, die als sicherheitskritisch markiert ist  
  
-   Gibt einen Typ, der als sicherheitskritisch markiert ist  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein Codeelement, die mit dem <xref:System.Security.SecurityCriticalAttribute> -Attribut ist sicherheitskritisch. Eine transparente Methode kann kein sicherheitskritisches Element verwenden. Wenn ein transparenter Typ versucht, einen sicherheitskritischen Typ zu verwenden eine <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , oder <xref:System.FieldAccessException> ausgelöst wird.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, führen Sie eine der folgenden:  
  
-   Markieren Sie das Code-Element, das den sicherheitskritischen Code mit verwendet die <xref:System.Security.SecurityCriticalAttribute> Attribut  
  
     \- oder –  
  
-   Entfernen Sie die <xref:System.Security.SecurityCriticalAttribute> Attribut aus der Codeelemente, die als sicherheitskritisch markiert sind, und markieren Sie sie mit stattdessen die <xref:System.Security.SecuritySafeCriticalAttribute> oder <xref:System.Security.SecurityTransparentAttribute> Attribut.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Eine transparente Methode versucht, in den folgenden Beispielen wird eine sicherheitskritische generische Auflistung, ein sicherheitskritisches Feld und eine wichtige Methode zu verweisen.  
  
 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>