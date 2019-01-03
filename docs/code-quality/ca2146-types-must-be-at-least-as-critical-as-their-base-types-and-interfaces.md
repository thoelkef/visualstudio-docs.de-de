---
title: 'CA2146: Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen sein.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 785c31d3d6d58215936e69d0c8034be955c9afd7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899888"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen sein.

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein transparenter Typ wird abgeleitet von einem Typ, die mit der <xref:System.Security.SecuritySafeCriticalAttribute> oder <xref:System.Security.SecurityCriticalAttribute>, oder ein Typ, der mit markiert ist die <xref:System.Security.SecuritySafeCriticalAttribute> Attribut stammt von einem Typ, die mit der <xref:System.Security.SecurityCriticalAttribute> Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird ausgelöst, wenn ein abgeleiteter Typ über ein Sicherheitstransparenzattribut verfügt, das nicht so wichtig wie der Basistyp oder die implementierte Schnittstelle ist. Nur wichtige Typen können von wichtigen Basistypen abgeleitet werden oder kritische Schnittstellen implementieren, und nur kritische oder sicherheitskritische Typen können von sicherheitskritischen Basistypen abgeleitet werden oder sicherheitskritische Schnittstellen implementieren. Verstöße gegen diese Regel in Transparenz der Ebene 2 führen eine <xref:System.TypeLoadException> für den abgeleiteten Typ.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verletzung zu beheben, markieren Sie die abgeleiteten oder implementierenden Typ mit einem Transparenzattribut, das mindestens genauso kritisch sein wie der Basistyp oder die Schnittstelle ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]