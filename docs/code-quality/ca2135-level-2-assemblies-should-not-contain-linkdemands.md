---
title: 'CA2135: Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d466a508eade835563627a829f937416a24972a0
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920640"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Eine Klasse oder ein Klassenmember verwendet <xref:System.Security.Permissions.SecurityAction> in einer Anwendung, die Sicherheit auf Ebene 2 verwendet.

## <a name="rule-description"></a>Regelbeschreibung
LinkDemands sind im Sicherheitsregelsatz der Ebene 2 veraltet. Anstatt LinkDemand zum Erzwingen der Sicherheit bei Just-in-time (JIT)-Kompilierungszeit zu verwenden, markieren Sie die Methoden, Typen und <xref:System.Security.SecurityCriticalAttribute> Felder mit dem-Attribut.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, entfernen <xref:System.Security.Permissions.SecurityAction> Sie den, und markieren Sie den Typ <xref:System.Security.SecurityCriticalAttribute> oder Member mit dem-Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Im folgenden Beispiel sollte das <xref:System.Security.Permissions.SecurityAction> entfernt und die-Methode mit dem <xref:System.Security.SecurityCriticalAttribute> -Attribut markiert werden.

[!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]