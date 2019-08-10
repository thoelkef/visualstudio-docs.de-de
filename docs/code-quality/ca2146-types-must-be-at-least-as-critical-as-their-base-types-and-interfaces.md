---
title: 'CA2146: Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a70e999505bd900a7b3d89693ef4f6a1cef9de7d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920427"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen.

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein transparenter Typ wird von einem Typ <xref:System.Security.SecuritySafeCriticalAttribute> abgeleitet, der mit <xref:System.Security.SecurityCriticalAttribute>oder gekennzeichnet ist, oder ein Typ, der mit dem <xref:System.Security.SecuritySafeCriticalAttribute> -Attribut markiert ist, wird von einem Typ abgeleitet, der mit <xref:System.Security.SecurityCriticalAttribute> dem-Attribut markiert ist.

## <a name="rule-description"></a>Regelbeschreibung
Diese Regel wird ausgelöst, wenn ein abgeleiteter Typ über ein Sicherheitstransparenzattribut verfügt, das nicht so wichtig wie der Basistyp oder die implementierte Schnittstelle ist. Nur wichtige Typen können von wichtigen Basistypen abgeleitet werden oder kritische Schnittstellen implementieren, und nur kritische oder sicherheitskritische Typen können von sicherheitskritischen Basistypen abgeleitet werden oder sicherheitskritische Schnittstellen implementieren. Verstöße gegen diese Regel in der Transparenz der Ebene 2 führen <xref:System.TypeLoadException> zu einer für den abgeleiteten Typ.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um diese Verletzung zu beheben, markieren Sie den abgeleiteten oder implementierenden Typ mit einem Transparenz Attribut, das mindestens so kritisch ist wie der Basistyp oder die Schnittstelle.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
[!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]