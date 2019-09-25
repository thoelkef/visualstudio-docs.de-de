---
title: 'CA2141: Transparente Methoden dürfen keine LinkDemands erfüllen'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0365d82917b8cfbaf291d557a6ac2d95c220562a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232120"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: Transparente Methoden dürfen keine LinkDemands erfüllen

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Eine Sicherheits transparente Methode ruft eine Methode in einer Assembly auf, die nicht mit dem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> -Attribut (APTCA) markiert ist, oder eine Sicherheits transparente <xref:System.Security.Permissions.SecurityAction> Methode erfüllt einen `.LinkDemand` für einen Typ oder eine Methode.

## <a name="rule-description"></a>Regelbeschreibung
Das erfüllen von LinkDemand ist ein sicherheitssensibler Vorgang, der eine unbeabsichtigte Erhöhung von Berechtigungen verursachen kann. Sicherheits transparenter Code muss linkrequirements nicht erfüllen, da er nicht denselben Sicherheits Überwachungsanforderungen unterliegt wie der sicherheitskritische Code. Transparente Methoden in Assemblys für sicherheitsregelsatz der Ebene 1 bewirken, dass alle verknüpften linkanforderungen zur Laufzeit in vollständige Anforderungen konvertiert werden. Dies kann zu Leistungsproblemen führen. In Assemblys der sicherheitsregelsatz-Ebene 2 können transparente Methoden im JIT-Compiler (Just-in-Time) nicht kompiliert werden, wenn Sie versuchen, einen LinkDemand zu erfüllen.

In Assemblys, die die Sicherheit der Ebene 2 verwenden, löst der Versuch einer Sicherheits transparenten Methode, einen LinkDemand-oder eine Methode in einer nicht-APTCA-Assembly zu erfüllen, eine <xref:System.MethodAccessException>aus; in Assemblys der Ebene 1 wird der LinkDemand zu einer vollständigen Anforderung

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Zugriffsmethode <xref:System.Security.SecurityCriticalAttribute> mit <xref:System.Security.SecuritySafeCriticalAttribute> dem-Attribut oder-Attribut, oder entfernen Sie LinkDemand aus der Methode, auf die zugegriffen wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
In diesem Beispiel versucht eine transparente Methode, eine Methode aufzurufen, die über einen LinkDemand verfügt. Diese Regel wird in diesem Code ausgelöst.

[!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]