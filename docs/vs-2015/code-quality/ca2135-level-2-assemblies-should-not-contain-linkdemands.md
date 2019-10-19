---
title: 'CA2135: Assemblys der Ebene 2 dürfen keine LinkDemand-Zeichen enthalten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1248ac41a757ba2fc26ef0659c0f93ee325bc605
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602944"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Assemblys der Stufe 2 dürfen keine LinkDemands enthalten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Klasse oder ein Klassenmember verwendet eine <xref:System.Security.Permissions.SecurityAction> in einer Anwendung, die Sicherheit auf Ebene 2 verwendet.

## <a name="rule-description"></a>Regelbeschreibung
 LinkDemands sind im Sicherheitsregelsatz der Ebene 2 veraltet. Anstatt LinkDemand zum Erzwingen der Sicherheit bei Just-in-time (JIT)-Kompilierungszeit zu verwenden, markieren Sie die Methoden, Typen und Felder mit dem <xref:System.Security.SecurityCriticalAttribute>-Attribut.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie die <xref:System.Security.Permissions.SecurityAction>, und markieren Sie den Typ oder Member mit dem Attribut <xref:System.Security.SecurityCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel sollte der <xref:System.Security.Permissions.SecurityAction> entfernt werden, und die-Methode wird mit dem <xref:System.Security.SecurityCriticalAttribute>-Attribut gekennzeichnet.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]
