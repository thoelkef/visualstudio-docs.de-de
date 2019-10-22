---
title: 'CA2147: transparente Methoden dürfen keine Sicherheits Bestätigungen verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f2bd0042b6f9a8e46939ab34c86294218fb79f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610163"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Transparente Methoden dürfen keine Sicherheitsassertionen verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Code, der als <xref:System.Security.SecurityTransparentAttribute> gekennzeichnet ist, verfügt nicht über ausreichende Berechtigungen für die Bestätigung.

## <a name="rule-description"></a>Regelbeschreibung
 Mit dieser Regel werden alle Methoden und Typen in einer Assembly analysiert, die entweder 100% transparent oder gemischt transparent/kritisch ist, und alle deklarativen oder imperativen Verwendungsmöglichkeiten von <xref:System.Security.CodeAccessPermission.Assert%2A> werden.

 Zur Laufzeit bewirken alle Aufrufe von <xref:System.Security.CodeAccessPermission.Assert%2A> aus transparentem Code, dass eine <xref:System.InvalidOperationException> ausgelöst wird. Dies kann sowohl in 100% transparenten Assemblys als auch in gemischten transparenten/kritischen Assemblys auftreten, in denen eine Methode oder ein Typ als transparent deklariert ist, aber eine deklarative oder imperative Bestätigung enthält.

 Der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2,0 hat eine Funktion mit dem Namen " *Transparenz*" eingeführt. Einzelne Methoden, Felder, Schnittstellen, Klassen und Typen können entweder transparent oder kritisch sein.

 Transparenter Code ist nicht berechtigt, Sicherheits Privilegien zu erhöhen. Aus diesem Grund werden alle gewährten Berechtigungen automatisch an die Aufrufer-oder Host Anwendungsdomäne übermittelt. Beispiele für Erweiterungen sind Assert, LinkDemand, SuppressUnmanagedCode und `unsafe` Code.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um das Problem zu beheben, markieren Sie entweder den Code, der den Assert aufruft, mit dem <xref:System.Security.SecurityCriticalAttribute>, oder entfernen Sie den Assert.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Meldung von dieser Regel.

## <a name="example"></a>Beispiel
 Dieser Code schlägt fehl, wenn `SecurityTestClass` transparent ist, wenn die `Assert`-Methode eine <xref:System.InvalidOperationException> auslöst.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Beispiel
 Eine Möglichkeit besteht darin, die SecurityTransparentMethod-Methode im folgenden Beispiel Code Review. wenn die Methode für die Rechte Erweiterung als sicher eingestuft wird, ist Mark SecurityTransparentMethod mit Secure-Critical erforderlich. Dies erfordert eine ausführliche, vollständige und fehlerfreie Sicherheit. Audit muss für die Methode mit allen Aufrufen erfolgen, die innerhalb der Methode unter der Assert-Methode auftreten:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Eine andere Möglichkeit besteht darin, die Assert-Berechtigung aus dem Code zu entfernen und allen nachfolgenden Datei-e/a-Berechtigungen das übernehmen von SecurityTransparentMethod an den Aufrufer zu gestatten Dies ermöglicht Sicherheitsüberprüfungen. In diesem Fall wird in der Regel keine Sicherheitsüberprüfung benötigt, da die Berechtigungsanforderungen an den Aufrufer und/oder die Anwendungsdomäne weitergeleitet werden. Berechtigungsanforderungen werden durch die Sicherheitsrichtlinie, die Hostingumgebung und die Berechtigungen zum Gewähren von Code Quellen streng gesteuert.

## <a name="see-also"></a>Siehe auch
 [Sicherheitswarnungen](../code-quality/security-warnings.md)
