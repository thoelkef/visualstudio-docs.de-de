---
title: "CA2147: Transparente Methoden dürfen keine Sicherheitsassertionen verwenden bestätigt | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 38ac5492c987515c7c6504c91d2e035f8b8645ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Transparente Methoden dürfen keine Sicherheitsassertionen verwenden
|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Code mit der Kennzeichnung <xref:System.Security.SecurityTransparentAttribute> ist nicht über ausreichende Berechtigungen für Assertions erteilt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel analysiert alle Methoden und Typen in einer Assembly, die entweder 100 % transparenten oder aus einer Kombination aus transparentem und kritischem alle deklarativen oder imperativen Verwendung von <xref:System.Security.CodeAccessPermission.Assert%2A>.  
  
 Zur Laufzeit werden alle Aufrufe von <xref:System.Security.CodeAccessPermission.Assert%2A> aus transparentem Code bewirkt, dass eine <xref:System.InvalidOperationException> ausgelöst wird. Dies kann auftreten, in beide 100 % transparente Assemblys sowie in gemischten transparent/kritisch Assemblys, in denen eine Methode oder generischen Typ transparent deklariert wird, aber eine Assertion deklarative oder imperative enthält.  
  
 Die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 eingeführt, ein Feature, mit dem Namen *Transparenz*. Einzelne Methoden, Felder, Schnittstellen, Klassen und Typen können entweder sicherheitstransparent oder sicherheitsrelevant sein.  
  
 Transparenter Code ist nicht zulässig, um die Sicherheit für die rechteerweiterung. Aus diesem Grund werden keine Berechtigungen erteilt oder angeforderten automatisch über den Code in der Anwendungsdomäne Aufrufer oder Host übergeben. Geschieht Asserts, LinkDemands, SuppressUnmanagedCode vermerkt, Beispiele und `unsafe` Code.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um das Problem zu beheben, markieren Sie entweder den Code, der aufgerufen wird, den Assert mit der <xref:System.Security.SecurityCriticalAttribute>, oder Entfernen der Assertion.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Meldung von dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Dieser Code schlägt fehl, wenn `SecurityTestClass` transparent ist, während die `Assert` -Methode löst eine <xref:System.InvalidOperationException>.  
  
 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Eine Möglichkeit besteht, Code Review der SecurityTransparentMethod-Methode im folgenden Beispiel, und wenn die Methode für die rechteerweiterung sicher betrachtet wird, markieren Sie SecurityTransparentMethod mit secure kritischen dies erfordert, dass eine detaillierte, vollständig und fehlerfrei-Sicherheit Audit muss auf die Methode sowie jeder Aufruf Sicherheitssperre ausgeführt werden, die innerhalb der Methode unter die Assertion auftreten:  
  
 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]  
  
 Eine weitere Option ist die Assertion aus dem Code entfernt, und lassen Sie alle nachfolgenden Datei-e/a-Berechtigung Forderungen Fluss hinter SecurityTransparentMethod an den Aufrufer. Dadurch wird überprüft. Keine sicherheitsüberwachung ist in diesem Fall normalerweise erforderlich, da die Berechtigung Forderungen an den Aufrufer und/oder der Anwendungsdomäne übergeben werden. Berechtigung Forderungen werden durch Sicherheitsrichtlinie hostumgebung, und Code-Source-berechtigungszuweisungen eng gesteuert.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitswarnungen](../code-quality/security-warnings.md)