---
title: 'CA2147: Transparente Methoden dürfen keine Sicherheitsassertionen verwenden Assert-Vorgänge | Microsoft-Dokumentation'
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
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 29681e6b43b3c8e71f10393cbaec715c33a89a93
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589572"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Transparente Methoden dürfen keine Sicherheitsassertionen verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2147: Transparente Methoden dürfen keine Sicherheitsassertionen verwenden bestätigt](https://docs.microsoft.com/visualstudio/code-quality/ca2147-transparent-methods-may-not-use-security-asserts).

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Code mit der Kennzeichnung <xref:System.Security.SecurityTransparentAttribute> ist nicht über ausreichende Berechtigungen für Assertions erteilt.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel analysiert alle Methoden und Typen in einer Assembly wird entweder 100 % transparente oder eine gemischte transparent/kritisch ist, und kennzeichnet die Nutzung von deklarativen oder imperativen <xref:System.Security.CodeAccessPermission.Assert%2A>.

 Zur Laufzeit werden alle Aufrufe von <xref:System.Security.CodeAccessPermission.Assert%2A> aus transparentem Code führt dazu, dass eine <xref:System.InvalidOperationException> ausgelöst wird. Dies kann auftreten, in beiden 100 % transparente Assemblys sowie im gemischten transparent/kritisch Assemblys, in denen eine Methode oder der Typ wird transparent deklariert, aber eine deklarative oder imperative Assertion enthält.

 Die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 eingeführt, ein Feature namens *Transparenz*. Einzelne Methoden, Felder, Schnittstellen, Klassen und Typen können entweder sicherheitstransparent oder sicherheitsrelevant sein.

 Transparenter Code ist nicht zulässig, um die Sicherheit für die rechteerweiterung. Aus diesem Grund werden keine Berechtigungen erteilt oder angeforderten automatisch durch den Code an die Anwendungsdomäne Aufrufer oder Host übergeben. Anforderungen für erhöhte Rechte Asserts, LinkDemands, SuppressUnmanagedCode vermerkt, Beispiele und `unsafe` Code.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um das Problem zu beheben, markieren Sie entweder den Code, den die Assertion aufgerufen, der <xref:System.Security.SecurityCriticalAttribute>, oder entfernen Sie die Assertion.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Meldung von dieser Regel.

## <a name="example"></a>Beispiel
 Dieser Code schlägt fehl, wenn `SecurityTestClass` transparent ist, während die `Assert` -Methode löst eine <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Beispiel
 Eine Möglichkeit ist, codereviews die SecurityTransparentMethod-Methode im folgenden Beispiel, und wenn die Methode für die Erhöhung der Rechte sicher erachtet wird, markieren Sie SecurityTransparentMethod mit sicherheitskritisch dies erfordert, dass eine ausführliche, vollständig und fehlerfrei-Sicherheit Audit muss für die Methode zusammen mit alle erläuterungen ausgeführt werden, die in der Methode unter die Assertion auftreten:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Eine weitere Möglichkeit ist die Assertion aus dem Code entfernt, und lassen Sie alle nachfolgenden Datei-e/a-Berechtigung Anforderungen Datenfluss über SecurityTransparentMethod an den Aufrufer. Dadurch können sicherheitsüberprüfungen. Keine sicherheitsüberwachung ist in diesem Fall in der Regel erforderlich, da die berechtigungsanforderungen für den Aufrufer und/oder der Anwendungsdomäne übergeben werden. Berechtigungsanforderungen werden genau durch Sicherheitsrichtlinien, hosting-Umgebung und Code-Source-Berechtigungen gesteuert.

## <a name="see-also"></a>Siehe auch
 [Sicherheitswarnungen](../code-quality/security-warnings.md)



