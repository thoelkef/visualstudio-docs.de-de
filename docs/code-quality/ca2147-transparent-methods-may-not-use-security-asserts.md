---
title: 'CA2147: Transparente Methoden dürfen keine Sicherheitsassertionen verwenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca9047866b5b8f030ee8e1f5a043683234edeb72
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859535"
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
 Diese Regel analysiert alle Methoden und Typen in einer Assembly, die entweder 100 % transparente oder eine gemischte transparent/kritisch ist, und kennzeichnet die Nutzung von deklarativen oder imperativen <xref:System.Security.CodeAccessPermission.Assert%2A>.

 Zur Laufzeit werden alle Aufrufe von <xref:System.Security.CodeAccessPermission.Assert%2A> aus transparentem Code führt dazu, dass eine <xref:System.InvalidOperationException> ausgelöst wird. Dies kann auftreten, in beiden 100 % transparente Assemblys sowie im gemischten transparent/kritisch Assemblys, in denen eine Methode oder der Typ wird transparent deklariert, aber eine deklarative oder imperative Assertion enthält.

 .NET Framework 2.0 eingeführt, ein Feature namens *Transparenz*. Einzelne Methoden, Felder, Schnittstellen, Klassen und Typen können entweder sicherheitstransparent oder sicherheitsrelevant sein.

 Transparenter Code ist nicht zulässig, um die Sicherheit für die rechteerweiterung. Aus diesem Grund werden keine Berechtigungen erteilt oder angeforderten automatisch durch den Code an die Anwendungsdomäne Aufrufer oder Host übergeben. Anforderungen für erhöhte Rechte Asserts, LinkDemands, SuppressUnmanagedCode vermerkt, Beispiele und `unsafe` Code.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um das Problem zu beheben, markieren Sie entweder den Code, der die Assertion aufgerufen der <xref:System.Security.SecurityCriticalAttribute>, oder entfernen Sie die Assertion.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Meldung von dieser Regel.

## <a name="example"></a>Beispiel
 Dieser Code schlägt fehl, wenn `SecurityTestClass` transparent ist, während die `Assert` -Methode löst eine <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Beispiel
 Eine Möglichkeit ist, codereviews die SecurityTransparentMethod-Methode im folgenden Beispiel, und wenn die Methode für die Erhöhung der Rechte sicher erachtet wird, markieren SecurityTransparentMethod, mit sicherheitskritisch. Dies erfordert, dass eine ausführliche, vollständig und fehlerfrei sicherheitsüberwachung für die Methode zusammen mit alle erläuterungen ausgeführt werden muss, die in der Methode unter die Assertion auftreten:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 Eine weitere Möglichkeit ist die Assertion aus dem Code entfernt, und lassen Sie alle nachfolgenden Datei-e/a-Berechtigung Anforderungen Datenfluss über SecurityTransparentMethod an den Aufrufer. Dadurch können sicherheitsüberprüfungen. In diesem Fall ist keine sicherheitsüberwachung benötigt, da die berechtigungsanforderungen für den Aufrufer und/oder der Anwendungsdomäne übergeben werden. Berechtigungsanforderungen werden genau durch Sicherheitsrichtlinien, hosting-Umgebung und Code-Source-Berechtigungen gesteuert.

## <a name="see-also"></a>Siehe auch
 [Sicherheitswarnungen](../code-quality/security-warnings.md)