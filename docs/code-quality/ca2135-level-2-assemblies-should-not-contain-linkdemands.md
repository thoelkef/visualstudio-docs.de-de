---
title: 'CA2135: Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 61f41a47b7fbb27e1811bd2c9888baf01143a50f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904101"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Klasse oder Klassenmember verwendet eine <xref:System.Security.Permissions.SecurityAction> in einer Anwendung, die Sicherheit der Ebene 2 verwendet wird.

## <a name="rule-description"></a>Regelbeschreibung
 LinkDemands sind im Sicherheitsregelsatz der Ebene 2 veraltet. Markieren Sie, statt LinkDemands zur Erzwingung von Sicherheit zur just-in-Time (JIT)-Kompilierungszeit zu erzwingen, die Methoden, Typen und Felder mit den <xref:System.Security.SecurityCriticalAttribute> Attribut.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen die <xref:System.Security.Permissions.SecurityAction> und markieren Sie den Typ oder Member mit dem <xref:System.Security.SecurityCriticalAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel die <xref:System.Security.Permissions.SecurityAction> entfernt werden soll, und die Methode gekennzeichnet, mit der <xref:System.Security.SecurityCriticalAttribute> Attribut.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]