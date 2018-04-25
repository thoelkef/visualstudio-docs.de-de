---
title: 'CA2146: Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d480b3b9fc2d6d294f13b15742e79c118ffec8f6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen
|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein transparenter Typ stammt von einem Typ, der mit gekennzeichnet ist die <xref:System.Security.SecuritySafeCriticalAttribute> oder die <xref:System.Security.SecurityCriticalAttribute>, oder ein Typ, der mit gekennzeichnet ist die <xref:System.Security.SecuritySafeCriticalAttribute> Attribut stammt von einem Typ, die mit der <xref:System.Security.SecurityCriticalAttribute> Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird ausgelöst, wenn ein abgeleiteter Typ über ein Sicherheitstransparenzattribut verfügt, das nicht so wichtig wie der Basistyp oder die implementierte Schnittstelle ist. Nur wichtige Typen können von wichtigen Basistypen abgeleitet werden oder kritische Schnittstellen implementieren, und nur kritische oder sicherheitskritische Typen können von sicherheitskritischen Basistypen abgeleitet werden oder sicherheitskritische Schnittstellen implementieren. Verstöße gegen diese Regel in Transparenz der Ebene 2 führen eine <xref:System.TypeLoadException> für den abgeleiteten Typ.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verstoß zu beheben, markieren Sie die abgeleiteten oder implementierenden Typ mit einem Transparenzattribut, das über mindestens so wichtig wie der Basistyp oder die Schnittstelle ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]